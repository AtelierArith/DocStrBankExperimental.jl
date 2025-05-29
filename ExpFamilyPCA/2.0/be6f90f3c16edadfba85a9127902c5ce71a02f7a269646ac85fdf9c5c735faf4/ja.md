```
fit!(epca::EPCA, X::AbstractMatrix{T}; maxiter::Integer = 100, verbose::Bool = false, steps_per_print::Integer = 10) where T <: Real
```

データセット `X` に対して EPCA モデルをフィットします。この関数は、EPCA 構造体を作成した後、または追加のデータでトレーニングを続ける場合に呼び出してください。

EPCA オブジェクトを作成した後、または新しいデータにフィットさせたいときに呼び出す必要があります。

!!! warning
    デフォルトの `fit!` は、データセットのサイズやモデルの複雑さに応じて長い実行時間がかかる場合があります。実行時間とモデルのパフォーマンスのバランスをより良くするために、冗長性 (`verbose`) と反復回数 (`maxiter`) を調整することを検討してください。


# 引数

  * `epca::EPCA`: EPCA モデル。
  * `X::AbstractMatrix{T}`: (`n`, `indim`) - 入力トレーニングデータ行列。行は観測値、列は特徴または変数です。

# キーワード引数

  * `maxiter::Integer = 100`: 損失最小化中に実行される最大反復回数。デフォルトは `100` です。早期に収束する場合があります。
  * `verbose::Bool = false`: 最適化の進行状況を印刷するかどうかを示すフラグ。`true` に設定すると、指定された間隔 (`steps_per_print`) で損失値と反復番号が印刷されます。デフォルトは `false` です。
  * `steps_per_print::Integer = 10`: `verbose` が `true` に設定されているときに、印刷された進行状況の更新の間の反復回数。たとえば、`steps_per_print` が `10` の場合、進行状況は10回の反復ごとに印刷されます。デフォルトは `10` です。

# 戻り値

  * `A::AbstractMatrix{T}`: (`n`, `outdim`) - 圧縮データ。

# 使用法

**入力:**

```julia
using ExpFamilyPCA
using Random; Random.seed!(1)

# モデルを作成
indim = 10  # 入力次元
outdim = 5  # 出力次元
epca = BernoulliEPCA(indim, outdim)

# ランダムなトレーニングデータを生成
n = 100
X = rand(0:1, n, indim)

# データにモデルをフィット
A = fit!(epca, X; maxiter=200, verbose=true, steps_per_print=50);
```

**出力:**

```@repl
Iteration: 1/200 | Loss: 31.7721864082419
Iteration: 50/200 | Loss: 11.07389383509631
Iteration: 100/200 | Loss: 10.971490262772905
Iteration: 150/200 | Loss: 10.886018474442618
Iteration: 200/200 | Loss: 10.718703556787007
```
