```
interpolate_fn(
    f::Function,
    x_vector::Vector{<:Union{VariableRef,AffExpr}},
    points::T where {T<:Matrix};
    method::Symbol = :default,
)
```

関数 `f` を変数（またはアフィン式）のセットに対して補間する関数です。`points` 行列の列数は `x_vector` の長さと同じである必要があります。

### 必須引数

`f` は、`x_vector` と同じ長さの引数ベクトルを取る可能性のある多次元関数です。

`x_vector` は、`f` の入力ベクトルである変数または式のベクトルです。

`points` は、関数のサンプルポイントを指定する `Matrix` です。

### オプション引数

`method` は、定式化方法であり、`:convex`、`:SOS1`、`:binary` または `:bisection` に設定できます。
