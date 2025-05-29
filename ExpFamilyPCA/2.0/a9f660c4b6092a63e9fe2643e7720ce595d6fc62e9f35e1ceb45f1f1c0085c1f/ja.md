```
compress(epca::EPCA, X::AbstractMatrix{T}; maxiter::Integer = 100, verbose::Bool = false, steps_per_print::Integer = 10) where T <: Real
```

入力データ `X` を EPCA モデルで圧縮します。

# 引数

  * `epca::EPCA`: フィットされた EPCA モデル。[1] `compress` の前に `fit!` を呼び出す必要があります。
  * `X::AbstractMatrix{T}`: （`n`、`indim`）- 入力データ行列（トレーニングデータとは異なる場合があります）。行は観測値、列は特徴または変数です。

# キーワード引数

  * `maxiter::Integer = 100`: 損失最小化中に実行される最大反復回数。デフォルトは `100` です。早期に収束する場合があります。
  * `verbose::Bool = false`: 最適化の進捗を印刷するかどうかを示すフラグ。`true` に設定すると、指定された間隔（`steps_per_print`）で損失値と反復回数を印刷します。デフォルトは `false` です。
  * `steps_per_print::Integer = 10`: `verbose` が `true` に設定されているときに印刷される進捗更新の間の反復回数。たとえば、`steps_per_print` が `10` の場合、10 回の反復ごとに進捗が印刷されます。デフォルトは `10` です。

# 戻り値

  * `A::AbstractMatrix{T}`: （`n`、`outdim`）- 圧縮されたデータ。

# 使用法

```julia
# ランダムなテストデータを生成
m = 10
Y = rand(0:1, m, indim)

# 前の例からのフィットされたモデルを使用してテストデータを圧縮
Y_compressed = compress(epca, Y)
```

[1]: `fit!` の前に `compress` が呼び出されると、`X` はフィットされていない初期重みを使用して圧縮されます。
