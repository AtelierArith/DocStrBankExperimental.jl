```
create_cheatsheet(
    repo::GitHubRepo, file_contents::AbstractVector{<:AbstractDict};
    model = "gpt4o", special_instructions::AbstractString = "None.
```

",         template::Symbol = :CheatsheetCreator,         cost*tracker::Union{Nothing, Threads.Atomic{<:Real}} = nothing,         verbose::Bool = true, save*path::Union{Nothing, String, Bool} = nothing,         http_kwargs::NamedTuple = NamedTuple())

```
create_cheatsheet(repo::GitHubRepo;
    model = "gpt4o", cost_tracker::Union{Nothing, Threads.Atomic{<:Real}} = Threads.Atomic{Float64}(0.0),
    special_instructions::AbstractString = "None.
```

",         template::Symbol = :CheatsheetCreator,         verbose::Bool = true, save*path::Union{Nothing, String} = nothing,         ntasks::Int = 0,         http*kwargs::NamedTuple = NamedTuple())

Creates a cheatsheet for the given GitHub repository and file summaries.

Note: If you're getting rate limited by GitHub API, request a personal access token and set it as `ENV["GITHUB_API_KEY"]` (raised your limit to 5000 requests per hour).

# Arguments

  * `repo::GitHubRepo`: The repository to create a cheatsheet for.
  * `file_contents::AbstractVector{<:AbstractDict}`: The file contents or the summaries of the files in the repository. If not provided, the repository is scanned and the file summaries are created.
  * `model::String`: The model to use for the LLM call.
  * `special_instructions::AbstractString`: Special instructions for the AI to tweak the output.
  * `template::Symbol`: The template to use for the cheatsheet creation.
  * `cost_tracker::Union{Nothing, Threads.Atomic{<:Real}}`: A tracker to record the cost of the LLM calls.
  * `verbose::Bool`: Whether to print verbose output.
  * `save_path::Union{Nothing, String, Bool}`: The path to save the cheatsheet to. If `true`, the cheatsheet is auto-saved to a subdirectory called `llm-cheatsheets` in the current working directory.
  * `http_kwargs::NamedTuple`: Additional keyword arguments to pass to the `github_api` function influencing the HTTP requests.
  * `ntasks::Int`: The number of tasks to use for the asynchronous processing. If `0`, the number of tasks is set to the `asyncmap` default.

# Returns

  * `String`: The content of the cheatsheet.
