```
esum(arr::AbstractArray{T1,1}, type::T2) where {T1 <: Number, T2 <: SumHelper}
```

## 説明

無限級数の改善された推定値を、系列の和項 `arr` を入力として使用して計算します。メソッドは `type` を設定することで選択できます。累積和を単純に計算できない場合は、`csum_f` 関数を指定して部分和の1次元配列を取得することもできます。

## 使用法

```
esum(arr, r)
```

## 引数

  * **`arr`**    : 和項の `AbstractVector`。
  * **`type`**   : 限界の改善された推定を構築するための `SumHelper` のインスタンス。
  * **`csum_f`** : オプション。`arr` から部分和配列を構築する関数。

## 参照

[`esum_c`](@ref), [`Richardson`](@ref), [`Shanks`](@ref)。

## 例

```julia
using SeriesAcceleration

r = Richardson(1:5,0:3)
arr = S1_100 = 1 ./ (1:100) .^ 2
limit = esum(arr, r)
```
