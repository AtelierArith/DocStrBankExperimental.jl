```
create_project_here()
create_project_here(include_examples=false)
```

Create the folder structure for a MicroTracker project *in the current working directory*.

If `include_examples` is false, then example particle data and videos will not be included.

# Example

```julia-repl
julia> pwd()
"~/tutorial"

julia> create_project_here()
[ Info: New MicroTracker project created in ~/tutorial
```
