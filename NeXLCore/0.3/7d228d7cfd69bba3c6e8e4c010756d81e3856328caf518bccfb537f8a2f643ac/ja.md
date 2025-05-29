```
thin_film(prs::Pair{Material, Float64}...; substrate::Union{Nothing,Material} = nothing)
```

オプションのバルク基板上に1つ以上の薄膜からなるサンプルを構築します。
