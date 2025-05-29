```
interpolate_points(
    x_vector::Vector{<:Union{VariableRef,AffExpr}},
    points::T where {T<:Matrix};
    method::Symbol = :default,
)
```

変数（またはアフィン式）のセットに対して補間を行う関数です。`points` 行列の列数は `x_vector` の長さ以上である必要があります。余分な列については、新しい変数が定義され、その値が補間されます。

### 必須引数

`x_vector` 三角形分割が形成される変数または式のベクトル。

`points` 補間される点を指定する `Matrix` です。

### オプション引数

`method` 定式化方法で、`:convex`、`:SOS1`、`:binary` または `:bisection` に設定できます。
