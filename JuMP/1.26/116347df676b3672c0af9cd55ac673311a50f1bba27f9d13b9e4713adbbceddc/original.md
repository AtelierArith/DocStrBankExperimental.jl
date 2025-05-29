```
anonymous_name(::MIME, x::AbstractVariableRef)
```

The name to use for an anonymous variable `x` when printing.

## Example

```jldoctest
julia> model = Model();

julia> x = @variable(model);

julia> anonymous_name(MIME("text/plain"), x)
"_[1]"
```
