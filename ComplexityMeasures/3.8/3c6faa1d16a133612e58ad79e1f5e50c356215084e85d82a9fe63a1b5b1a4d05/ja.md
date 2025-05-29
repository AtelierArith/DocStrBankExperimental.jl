```
ValueBinning(b::AbstractBinning) <: OutcomeSpace
```

[`OutcomeSpace`](@ref) は、ビニングスキーム `b` に従ってデータの値をビニングし、ヒストグラム、すなわちビン内のポイントの頻度を正式に計算することに基づいています。このエイリアスは `VisitationFrequency` です。利用可能なビニングは [`AbstractBinning`](@ref) のサブタイプです。

`ValueBinning` 推定器は線対数時間計算量（`n log(n)`、ここで `n = length(x)`）と線形空間計算量（`l`、ここで `l = dimension(x)`）を持ちます。これにより、高次元データセットの確率（ヒストグラム）を小さなボックスサイズ `ε` でメモリオーバーフローなしに、最大のパフォーマンスで計算することができます。パフォーマンス上の理由から、返される確率は決して 0 を含まず、任意に順序付けられています。

```
ValueBinning(ϵ::Union{Real,Vector})
```

[`RectangularBinning`](@ref) と同じ入力を受け入れ、このビニングを直接初期化する便利なメソッドです。

## Outcomes

`ValueBinning` のアウトカムスペースは、`b` から構築されたユニークなビンです。各ビンはその左（最小値）コーナーによって識別されます。ビンは常に左閉右開区間 `[a, b)` であるためです。ビンはデータ単位であり、整数（直交座標インデックス単位）ではなく、入力データと同じ型の `SVector` として返されます。

便利のために、[`outcome_space`](@ref) は基礎となるビニングと同じ配列形式でアウトカムを返します（例：2D入力の場合は `Matrix`）。

[`FixedRectangularBinning`](@ref) の場合、[`outcome_space`](@ref) はビニングから明確に定義されますが、[`RectangularBinning`](@ref) の場合は入力 `x` も必要です。

## Implements

  * [`codify`](@ref)。順序が重要な入力をエンコードするために使用されます（例：時系列）。
