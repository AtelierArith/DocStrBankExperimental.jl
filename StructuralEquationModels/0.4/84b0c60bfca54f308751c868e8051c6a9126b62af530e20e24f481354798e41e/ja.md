```
SemFiniteDiff(;observed = SemObservedData, implied = RAM, loss = SemML, kwargs...)
```

専用の勾配とヘッセ行列の評価を有限差分近似に置き換える[`Sem`](@ref)のラッパーです。

# 引数

  * `observed`: `SemObserved`のサブタイプのオブジェクトまたはコンストラクタ。
  * `implied`: `SemImplied`のサブタイプのオブジェクトまたはコンストラクタ。
  * `loss`: `SemLossFunction`のサブタイプのオブジェクトまたはコンストラクタ; またはそのタプル。

次のフィールドを持つSemを返します。

  * `observed::SemObserved`: 観測データ、サンプル統計などを格納します。詳細は[`SemObserved`](@ref)を参照してください。
  * `implied::SemImplied`: Σ、μなどのモデル暗示統計を計算します。詳細は[`SemImplied`](@ref)を参照してください。
  * `loss::SemLoss`: 損失関数の合計の目的と勾配を計算します。詳細は[`SemLoss`](@ref)を参照してください。
