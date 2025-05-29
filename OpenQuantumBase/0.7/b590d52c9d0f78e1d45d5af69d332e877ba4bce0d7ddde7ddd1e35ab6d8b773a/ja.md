```julia
struct TimeDependentCoupling
```

単一の時間依存系バス結合演算子を定義します。これは $S(s)=∑f(s)×M$ として定義されます。キーワード引数 `unit` は単位を設定します – `:h` または `:ħ`。

# フィールド

  * `funcs`: 時間依存関数の1-D配列
  * `mats`: 定数行列の1-D配列

# 例

```julia-repl
julia> TimeDependentCoupling([(s)->s], [σz], unit=:ħ)
```
