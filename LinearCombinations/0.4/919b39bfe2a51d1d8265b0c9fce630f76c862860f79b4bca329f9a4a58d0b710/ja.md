```
is_domain(::Type{R}) where R -> Bool
```

`R` が既知の整域である場合は `true` を返し、それ以外の場合は `false` を返します。整域とは、零因子を持たない可換環です。

デフォルトでは、`is_domain` は `Real` および `Complex` のサブタイプに対してのみ `true` を返します。`is_domain(R) == true` の場合、時にはより効率的なアルゴリズムを選択できることがあります。

関連情報として [`has_char2`](@ref) も参照してください。
