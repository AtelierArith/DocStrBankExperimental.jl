```
map_coefficients(f::Function, p::AbstractPolynomialLike, nonzero = false)
```

与えられた多項式 `p` と同じ単項式を持つ多項式を返しますが、各係数 `α` は `f(α)` に置き換えられます。この関数がゼロを返す場合、その項は削除されます。非ゼロの入力に対して関数が決してゼロを返さないことが知られている場合、`nonzero` を `true` に設定することで小さな速度向上が得られます。

他にも [`map_coefficients!`](@ref) と [`map_coefficients_to!`](@ref) を参照してください。

### 例

`map_coefficients(α -> mod(3α, 6), 2x*y + 3x + 1)` を呼び出すと `3x + 3` が返されるはずです。
