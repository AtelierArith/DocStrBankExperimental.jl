```
GitHubRepo(url::String; paths = ["src", "docs/src", "README.md"],
    file_types = [".jl", ".md"])
```

Creates a `GitHubRepo` object to represent a target GitHub repository.

# Arguments

  * `url::String`: The URL of the GitHub repository.
  * `paths::Vector{String}`: The folders and files to scan.
  * `file_types::Vector{String}`: The file types to accept in the scan.

# Fields

  * `owner::String`: The owner of the repository.
  * `name::String`: The name of the repository.
  * `url::String`: The URL of the repository.
  * `paths::Vector{String}`: The folders and files to scan.
  * `file_types::Vector{String}`: The file types to accept in the scan.

Note: Files and folders are scanned recursively.

Key methods: `scan_github_path`, `create_cheatsheet`, `collect`.

  * `scan_github_path` is used to scan the repository and get the list of all relevant files.
  * `create_cheatsheet` is used to create a cheatsheet from the repository.
  * `collect` is used to collect the repository content into a single string (no summarization).

# Example

```julia
repo = GitHubRepo("https://github.com/username/repository")
files = scan_github_path(repo)
```

Let's create a cheatsheet and auto-save it to a file:

```julia
repo = GitHubRepo("https://github.com/username/repository")
cheatsheet = create_cheatsheet(repo; save_path = true)
```

Let's collect all the files in the repository (eg, for LLM calls):

```julia
repo = GitHubRepo("https://github.com/username/repository")
collated = collect(repo)
```
