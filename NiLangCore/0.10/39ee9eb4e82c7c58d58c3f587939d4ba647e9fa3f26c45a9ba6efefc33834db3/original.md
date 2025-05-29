```
@code_preprocess ex
```

Preprocess `ex` and return the symmetric reversible IR.

```jldoctest; setup=:(using NiLangCore)
julia> NiLangCore.rmlines(@code_preprocess if (x < 3, ~) x += exp(3.0) end)
:(if (x < 3, x < 3)
      x += exp(3.0)
  end)
```
