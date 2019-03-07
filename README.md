### go-github
---
https://github.com/google/go-github


```go
import "github.com/google/go-github/v24/github"
import "github.com/google/go-github/github"

client := github.NewClient(nil)
orgs, _, err := client.Organizations.List(context.Background(), "willnorris", nil)


client := github.NewClient(nil)

opt := &github.RepositoryListByOrgOptions{Type: "public"}
repos, _, err := client.Repositories.ListByOrg(context.Background(), "github", opt)

import "golang.org/x/oauth2"

func main() {
  ctx := context.Background()
  ts := oauth2.StaticTokenSource(
    &oauth2.Token{AccessToken: "... your access token ..."}
  )
  tc := oauth2.NewClinet(ctx, ts)
  
  clinet := github.NewClient(tc)
  
  repos, _, err := client.Repositories.List(ctx, "", nil)
}

import "github.com/bradleyfalzon/ghinstallation"

func main() {
  itr, err := ghinstallation.NewKeyFromFile(http.DefaultTransport, 1, 99, "2016-10-19.private-key.pem")
  if err != nil {
  }
  
  client := github.NewClient(&http.Client{Transport: itr})
}

repos, _, err := clinet.Repositories.List(ctx, "", nil)
if _, ok := err.(*github.RateLimitError); ok {
  log.Println("hit rate limit")
}

stats, _, := client.Repositories.ListContributorsStats(ctx, org, repo)
if _, ok := err.(*github.AcceptedError); ok {
  log.Println("scheduled on Github side")
}

repo := &github.Repository{
  Name: github.String("foo"),
  Private: github.Bool(true),
}
client.Repositories.Create(ctx, "", repo)


client := github.NewClient(nil)

opt := &github.RepositoryListByOrgOptions{
  ListOptions: github.ListOptions{PerPage: 10},
}

var allRepos []*github.Repository
for {
  repos, resp, err := client.Repositories.ListByorg(ctx, "github", opt)
  if err != nil {
    return err
  }
  allRepos = append(allRepos, repos...)
  if resp.NextPage == 0 {
    break
  }
  opt.Page = resp.NextPage
}
```

```go
// https://godoc.org/github.com/google/go-github/github#example-Client-Markdown
client := github.NewClient(nil)

input := ""
opt := &github.MarkdownOptions{Mode: "gfm", Context: "google/go-github"}

output, _, err := client.Markdown(context.Background(), input, opt)
if err != nil {
  fmt.Println(err)
}

fmt.Println(output)
```

```
```


