```
right_inverse(f)
```

単一入力単一出力関数 `f` が与えられたとき、その右逆関数 `g` を返します。これは `f` が全射である必要があります。関数に対して `right_inverse` が定義されている場合、`left_inverse` と `inverse` は定義されていない必要があり、エラーを返すべきです。`left_inverse(g)` も定義されており、`f` を返す必要があります。

参照：[ `inverse`](@ref)、[ `left_inverse`](@ref)、[ `@register_inverse`](@ref)。
