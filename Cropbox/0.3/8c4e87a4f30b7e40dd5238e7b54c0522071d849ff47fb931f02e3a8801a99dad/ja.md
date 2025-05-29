```
evaluate(obs, est; <キーワード引数>) -> 数値 | タプル
```

観測データ `obs` と推定データ `est` を評価指標の選択とともに比較します。

# 引数

  * `obs::DataFrame`: 評価に使用される観測データ。
  * `est::DataFrame`: シミュレーションからの推定データ。

# キーワード引数

## レイアウト

  * `index`: 出力のインデックス列を参照する変数。
  * `target`: 出力の非インデックス列を参照する変数。

## 評価

  * `metric=nothing`: 評価指標 (`:rmse`, `:nrmse`, `:mae`, `:mape`, `:ef`, `:dr`); デフォルトは RMSE。

参照: [`evaluate`](@ref)

# 例

```julia-repl
julia> obs = DataFrame(time = [1, 2, 3]u"hr", b = [10, 20, 30]u"g");

julia> est = DataFrame(time = [1, 2, 3]u"hr", b = [10, 20, 30]u"g", c = [11, 19, 31]u"g");

julia> evaluate(obs, est; index = :time, target = :b)
0.0 g

julia> evaluate(obs, est; index = :time, target = :b => :c)
1.0 g
```
