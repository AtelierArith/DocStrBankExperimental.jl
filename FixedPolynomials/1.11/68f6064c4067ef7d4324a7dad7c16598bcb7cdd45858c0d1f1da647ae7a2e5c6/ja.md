```
substitute(p::Polynomial, i, x)
```

`p`の変数のインデックス`i`を`x`の値で置き換えます。これは多項式の部分評価に使用できます。

### 例

```julia-repl
julia> substitute(x^2+3y, 2, 5)
x^2+15
```
