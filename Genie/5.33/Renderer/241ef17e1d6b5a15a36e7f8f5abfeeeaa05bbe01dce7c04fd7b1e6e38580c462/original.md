Sets redirect headers and prepares the `Response`. It accepts 3 parameters: 1 - Label of a Route (to learn more, see the advanced routes section) 2 - Default HTTP 302 Found Status: indicates that the provided resource will be changed to a URL provided 3 - Tuples (key, value) to define the HTTP request header

Example: julia> Genie.Renderer.redirect(:index, 302, Dict("Content-Type" => "application/json; charset=UTF-8"))

HTTP.Messages.Response: HTTP/1.1 302 Moved Temporarily Content-Type: application/json; charset=UTF-8 Location: /index

Redirecting you to /index
