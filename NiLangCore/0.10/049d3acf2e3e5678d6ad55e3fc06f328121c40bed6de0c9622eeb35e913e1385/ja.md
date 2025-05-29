```
@code_julia ex
```

`ex`の解釈された式を取得します。

```julia
julia> @code_julia x += exp(3.0)
quote
    var"##results#267" = ((PlusEq)(exp))(x, 3.0)
    x = var"##results#267"[1]
    try
        (NiLangCore.deanc)(3.0, var"##results#267"[2])
    catch e
        @warn "deallocate fail: `3.0 → var"##results#267"[2]`"
        throw(e)
    end
end

julia> @code_julia @invcheckoff x += exp(3.0)
quote
    var"##results#257" = ((PlusEq)(exp))(x, 3.0)
    x = var"##results#257"[1]
end
```
