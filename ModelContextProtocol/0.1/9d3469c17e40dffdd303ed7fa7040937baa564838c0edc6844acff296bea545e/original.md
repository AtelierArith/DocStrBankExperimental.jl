```
ResourceTemplate(; name::String, uri_template::String,
               mime_type::Union{String,Nothing}=nothing, description::String="")
```

Define a template for dynamically generating resources with parameterized URIs.

# Fields

  * `name::String`: Name of the resource template
  * `uri_template::String`: Template string with placeholders for parameters
  * `mime_type::Union{String,Nothing}`: MIME type of the generated resources
  * `description::String`: Human-readable description of the template
