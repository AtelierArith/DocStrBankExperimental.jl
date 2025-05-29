```
@code_preprocess ex
```

`ex`を前処理し、対称的で可逆なIRを返します。

```jldoctest; setup=:(using NiLangCore)
julia> NiLangCore.rmlines(@code_preprocess if (x < 3, ~) x += exp(3.0) end)
:(if (x < 3, x < 3)
      x += exp(3.0)
  end)
```
