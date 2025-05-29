```
inverse(f)
```

単一入力単一出力関数 `f` が与えられたとき、その逆関数 `g` を返します。これは `f` が全単射である必要があります。関数に対して `inverse` が定義されている場合、`left_inverse` と `right_inverse` は `inverse(f)` を返すべきです。`inverse(g)` も `f` を返すように定義されるべきです。

参照: [`left_inverse`](@ref), [`right_inverse`](@ref), [`@register_inverse`](@ref).
