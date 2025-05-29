```
Sem(;observed = SemObservedData, implied = RAM, loss = SemML, kwargs...)
```

基本的な `Sem` 型のコンストラクタ。すべての追加の kwargs は、観測、暗示、および損失フィールドのコンストラクタに渡されます。

# 引数

  * `observed`: サブタイプ `SemObserved` のオブジェクトまたはコンストラクタ。
  * `implied`: サブタイプ `SemImplied` のオブジェクトまたはコンストラクタ。
  * `loss`: サブタイプ `SemLossFunction` のオブジェクトまたはコンストラクタ; またはそのタプル。

フィールドを持つ Sem を返します

  * `observed::SemObserved`: 観測データ、サンプル統計などを格納します。詳細は [`SemObserved`](@ref) を参照してください。
  * `implied::SemImplied`: Σ、μ などのモデル暗示統計を計算します。詳細は [`SemImplied`](@ref) を参照してください。
  * `loss::SemLoss`: 損失関数の合計の目的関数と勾配を計算します。詳細は [`SemLoss`](@ref) を参照してください。

```
