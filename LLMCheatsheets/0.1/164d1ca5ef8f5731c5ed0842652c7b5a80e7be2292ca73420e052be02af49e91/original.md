```
scan_github_path(repo::GitHubRepo, path::String; verbose = true,
    http_kwargs::NamedTuple = NamedTuple())

scan_github_path(repo::GitHubRepo; verbose = true,
    http_kwargs::NamedTuple = NamedTuple())
```

Scans a specific path in a GitHub repository and returns a list of files it contains that meet the criteria in `repo`. Scans any nested folders recursively.

Note: If you're getting rate limited by GitHub, set the API key in `ENV["GITHUB_API_KEY"]`.

# Arguments

  * `repo::GitHubRepo`: The repository to scan.
  * `path::String`: The path to scan in the repository. If path is not provided, it will scan all paths in the repo object.
  * `verbose::Bool`: Whether to print verbose output.
  * `http_kwargs::NamedTuple`: Additional keyword arguments to pass to `github_api`.

# Returns

  * `Vector{JSON3.Object}`: A list of files and folders in the specified path.
