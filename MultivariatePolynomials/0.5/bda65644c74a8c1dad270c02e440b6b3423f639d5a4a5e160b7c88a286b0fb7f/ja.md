```
map_coefficients!(f::Function, p::AbstractPolynomialLike, nonzero = false)
```

`p`を変異させ、各係数`α`を`f(α)`で置き換えます。関数がゼロを返す場合、その項は削除されます。関数が非ゼロの入力に対してゼロを返さないことが知られている場合、`nonzero`を`true`に設定することで小さな速度向上が得られます。関数は`p`を返し、これは第二引数と同一です。

関連情報として[`map_coefficients`](@ref)および[`map_coefficients_to!`](@ref)を参照してください。

### 例

`p = 2x*y + 3x + 1`とし、`map_coefficients!(α -> mod(3α, 6), p)`の後、`p`は`3x + 3`に等しくなります。
