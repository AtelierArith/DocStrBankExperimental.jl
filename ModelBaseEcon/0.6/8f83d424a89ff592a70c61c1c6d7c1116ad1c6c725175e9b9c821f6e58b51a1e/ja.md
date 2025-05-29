```
add_equation!(model::Model, eqn_key::Symbol, expr::Expr; modelmodule::Module)
```

与えられたモジュールのコンテキスト内で与えられた式を処理し、それに対する Equation() インスタンスを作成し、モデルインスタンスに追加します。

通常、この関数を直接呼び出す必要はありません。これは [`@initialize`](@ref) の間に呼び出されます。
