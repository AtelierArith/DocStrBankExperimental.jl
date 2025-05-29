```
interpolate_fn(
    f::Function,
    x_vector::Vector{<:Union{VariableRef,AffExpr}},
    grid::Vector{<:Union{AbstractRange,Vector{<:Real}}};
    method::Symbol = :default,
)
```

関数 `f` を変数（またはアフィン式）のセットに対して補間する関数です。`grid` ベクトルは `x_vector` と同じ長さである必要があります。

### 必須引数

`f` は、`x_vector` と同じ長さの引数ベクトルを取る可能性のある多次元関数です。

`x_vector` は、`f` の入力ベクトルである変数または式のベクトルです。

`grid` は、関数 `f` のサンプルポイント（ベクトルの直積）を指定する範囲またはベクトルのベクトルです。

### オプション引数

`method` は、定式化方法であり、`:convex`、`:SOS1`、`:binary` または `:bisection` に設定できます。
