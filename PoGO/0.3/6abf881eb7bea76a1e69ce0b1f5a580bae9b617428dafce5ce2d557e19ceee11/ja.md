```
approximate(
    x::Union{VariableRef,AffExpr},
    func::Function,
    n::Int = 0;
    δ::Real = 0.0,
    method::Symbol = :default,
    type::Symbol = :interior,
    knots::Union{Nothing,Vector{Float64},Vector{Tuple{Float64,Symbol}}} = nothing,
    name::String = "",
)
```

任意の単変数関数の混合整数プログラミング定式化を定義する関数。

### 必須引数

`x` は `VariableRef` または `AffExpr` のいずれかの型であり、関数 `func` の入力変数です。

`func` は近似している関数です。

### 任意の引数

`n` はノット間でサンプリングされるポイントの数（`δ` が使用される場合は無視されます）。

`δ` はサンプルポイント間の最小距離です。

`method` は近似の方法です。これは `:binary`、`:echelon`、`:convex`、`:bisection`、`:SOS1` または `:SOS2` に設定できます。

`type` は近似が実際の関数をどのように制約するかを指定します。これは `:upper`、`:lower`、`:interior`、`tangent_cuts` または `:combined` に設定できます。

`knots` は関数の不連続点と変曲点をリストする必要があります。曲率が指定されている場合は提供できますが、指定されていない場合は自動的に決定されます。

`name` は作成された変数に意味のある名前を付けるために設定できます。
