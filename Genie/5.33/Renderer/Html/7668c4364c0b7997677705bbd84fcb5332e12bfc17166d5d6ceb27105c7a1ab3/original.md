```
html(data::String; context::Module = @__MODULE__, status::Int = 200, headers::HTTPHeaders = HTTPHeaders(), layout::Union{String,Nothing} = nothing, vars...) :: HTTP.Response
```

Parses the `data` input as HTML, returning a HTML HTTP Response.

# Arguments

  * `data::String`: the HTML string to be rendered
  * `context::Module`: the module in which the variables are evaluated (in order to provide the scope for vars). Usually the controller.
  * `status::Int`: status code of the response
  * `headers::HTTPHeaders`: HTTP response headers
  * `layout::Union{String,Nothing}`: layout file for rendering `data`

# Example

```jldoctest
julia> html("<h1>Welcome $(vars(:name))</h1>", layout = "<div><% @yield %></div>", name = "Adrian")
HTTP.Messages.Response:
"
HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8

<html><head></head><body><div><h1>Welcome Adrian</h1>
</div></body></html>"
```
