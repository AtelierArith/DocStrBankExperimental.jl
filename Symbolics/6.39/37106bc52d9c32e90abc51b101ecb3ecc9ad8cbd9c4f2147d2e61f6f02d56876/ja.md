```
left_inverse(f)
```

単一入力単一出力関数 `f` が与えられたとき、その左逆関数 `g` を返します。これは `f` が単射である必要があります。関数に対して `left_inverse` が定義されている場合、`right_inverse` と `inverse` は定義されていない必要があり、エラーを返すべきです。`right_inverse(g)` も定義されており、`f` を返すべきです。

参照: [`inverse`](@ref), [`right_inverse`](@ref), [`@register_inverse`](@ref).
