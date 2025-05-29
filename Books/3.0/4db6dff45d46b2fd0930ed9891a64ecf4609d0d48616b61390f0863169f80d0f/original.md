```
gen(
    [paths::Vector{String}],
    [block_number::Union{Nothing,Int}=nothing];
    call_html::Bool=true,
    fail_on_error::Bool=false,
    project="default",
    kwargs...
)
```

Populate the files in `_gen/` by calling the required methods. These methods are specified by the filename and will output to that filename. This allows the user to easily link code blocks to code. After calling the methods, this method will also call `html()` to update the site when `call_html == true`. The `kwargs...` is meant to ignore `M` so that `entr_gen` is a drop-in replacement for `gen`.
