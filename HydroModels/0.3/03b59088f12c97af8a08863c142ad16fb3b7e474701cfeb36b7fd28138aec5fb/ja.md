```
UnitHydrograph{N, ST} <: AbstractHydrograph
```

ユニットハイドログラフのルーティングコンポーネントを表します。

# フィールド

  * `uh_func::Function`: 時間とパラメータに基づいてユニットハイドログラフの形状を定義する関数。
  * `max_lag_func::Function`: パラメータに基づいて最大遅延時間を計算する関数。
  * `infos::NamedTuple`: メタデータ（入力、出力、パラメータ）。

# コンストラクタ

```julia
UnitHydrograph(inputs, params; uh_pairs, max_lag, outputs=[], configs=(solvetype=:DISCRETE, suffix=:_lag), name=nothing)
```

  * `inputs`, `params`, `outputs`: `Num`変数のベクトル。
  * `uh_pairs`: ピースワイズUHセグメントを定義する`Pair`のベクトル（`time_bound => expression`）。
  * `max_lag`: 最初のUHセグメントの上限。
  * `configs`: デフォルトの出力名のための`solvetype`（`:DISCRETE`または`:SPARSE`）と`suffix`を含むNamedTuple。
  * `name`: オプションのシンボル識別子。

# 注意事項

  * 型パラメータ`ST`は`solvetype`（`:DISCRETE`または`:SPARSE`）を反映します。
  * `uh_pairs`と`params`から`uh_func`と`max_lag_func`を生成します。
  * 定義されたユニットハイドログラフと入力時系列を畳み込むために使用されます。
