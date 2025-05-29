```
esum_c(carr::AbstractArray{T1,1}, type::T2) where {T1 <: Number, T2 <: SumHelper}
```

## 説明

累積和 `carr` を入力として使用して無限級数の改善された推定を計算します。メソッドは `type` を設定することで選択できます。詳細については、[`Richardson`](@ref)や[`Shanks`](@ref)を参照してください。技術的な理由から、アルゴリズムは内部で部分和を使用します。このメソッドは、部分和を自ら構築する[`esum`](@ref)メソッドよりも、より高速で柔軟なインターフェースを提供します。

## 使用法

```
esum_c(arr, r)
```

## 引数

  * **`carr`** : 各インデックスまでの部分和の `AbstractVector`。
  * **`type`** : 限界の改善された推定を構築するための `SumHelper` のインスタンス。

## 参照

[`esum`](@ref)、[`Richardson`](@ref)、[`Shanks`](@ref)。

## 例

```julia
using SeriesAcceleration

r = Richardson(1:5,0:3)
arr = cumsum(S1_100 = 1 ./ (1:100) .^ 2)
limit = esum_c(arr, r)
```
