```
power(
    x::Union{VariableRef,AffExpr},
    y::Union{VariableRef,AffExpr},
    n::Int = 0;
    method::Symbol = :default,
    type::Symbol = :interior,
    name::String = "",
)
```

与えられた変数またはアフィン式のペアに対して累乗の定式化（`x^y`）を定義する関数です。この関数は、`x` と `y` に基づいて最適な定式化を選択します。

### 必須引数

`x` と `y` は `VariableRef` または `AffExpr` のいずれかの型であり、`x^y` はモデル化される累乗関数です。

### オプション引数

`n` は、累乗が二つの平方の差を用いて近似される場合に使用されます。

`method` は、累乗が二つの平方の差を用いて近似される場合に使用されます。これは `:binary` `:echelon` `:SOS1` または `:SOS2` に設定できます。

`type` は、累乗が二つの平方の差を用いて近似される場合に使用されます。これは `:upper` `:lower` `:interior` `cutting_planes` または `:combined` に設定できます。

`name` は、作成された変数に意味のある名前を付けるために設定できます。
