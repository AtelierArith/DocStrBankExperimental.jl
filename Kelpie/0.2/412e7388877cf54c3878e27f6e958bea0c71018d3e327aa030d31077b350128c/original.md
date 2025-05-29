```
html(content...=nothing; kwargs...)
```

Creates a new HTML document filled with `content`.

# Example

```jldoctest
julia> import EzXML: prettyprint

julia> prettyprint(html())
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!DOCTYPE html SYSTEM "about:legacy-compat">
<html/>
```
