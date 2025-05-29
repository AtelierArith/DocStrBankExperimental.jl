```
interpolate(
    x_vector::Vector{<:Union{VariableRef,AffExpr}},
    points::Vector{<:Tuple},
    sets::Vector;
    update_bounds::Bool = false,
    method::Symbol = :default,
    name::String = "",
)
```

変数を制約して、`sets`で定義された点の集合の凸包内に収める関数です。

### 必須引数

`x_vector` 補間のドメインとして使用される変数または式のベクター

`points` 補間を定義する点のベクター; これらの点は実数だけでなく、変数や式を含むことができます。

`sets` `points`の各点に対して、`sets`はその点が属する集合の名前を含みます。

### オプション引数

`update_bounds` `true`に設定されている場合、`points`の値に基づいて`x_vector`のコンポーネントの上限と下限が更新されるべきです。

`method` 定式化方法を指定し、`:convex`、`:SOS1`、`:binary`または`:bisection`に設定できます。

`name` 作成された変数に意味のある名前を付けるために設定できます。
