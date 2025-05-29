```
GitHubRepo(;
    dir=mktempdir(),
    user=ENV["GITHUB_ACTOR"],
    token=ENV["GITHUB_TOKEN"],
    repo=ENV["GITHUB_REPOSITORY"],
    branch="skan"
)
```

Assuming that we run on a GitHub Runner, then no extra information is needed. The token and repo can be obtained via `GITHUB_TOKEN` and `GITHUB_REPOSITORY`. For public repositories, set `token` to the empty string `""`. `repo` is of the form `octocat/Hello-World`.
