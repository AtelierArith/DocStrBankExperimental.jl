```
html(viewfile::FilePath; layout::Union{Nothing,FilePath} = nothing,
      context::Module = @__MODULE__, status::Int = 200, headers::HTTPHeaders = HTTPHeaders(), vars...) :: HTTP.Response
```

Parses and renders the HTML `viewfile`, optionally rendering it within the `layout` file. Valid file format is `.html.jl`.

# Arguments

  * `viewfile::FilePath`: filesystem path to the view file as a `Renderer.FilePath`, ie `Renderer.filepath("/path/to/file.html.jl")` or `path"/path/to/file.html.jl"`
  * `layout::FilePath`: filesystem path to the layout file as a `Renderer.FilePath`, ie `Renderer.FilePath("/path/to/file.html.jl")` or `path"/path/to/file.html.jl"`
  * `context::Module`: the module in which the variables are evaluated (in order to provide the scope for vars). Usually the controller.
  * `status::Int`: status code of the response
  * `headers::HTTPHeaders`: HTTP response headers
