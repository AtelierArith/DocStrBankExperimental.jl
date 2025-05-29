```
UncertainIndexValueDataset{
    IDXTYP<:AbstractUncertainIndexDataset, 
    VALSTYP<:AbstractUncertainValueDataset}
```

不確実な `indices`（例：時間、深さ、順序など）と不確実な `values` のセットで構成される一般的なデータセットタイプです。

i 番目のインデックスは i 番目の値に対応すると仮定されます。たとえば、`data` が `UncertainIndexValueDataset` のインスタンスである場合、

  * `data.indices[2]` は値 `data.values[2]` のインデックスです。
  * `data.values[7]` はインデックス `data.indices[7]` の値です。
  * `data[3]` はインデックス-値のタプル `(data.indices[3], data.values[3])` です。

## フィールド

  * **`indices::T where {T <: AbstractUncertainIndexDataset}`**: 不確実なインデックスで、あるタイプの不確実なインデックスデータセットによって表されます。
  * **`values::T  where {T <: AbstractUncertainValueDataset}`**: 不確実な値で、あるタイプの不確実な値データセットによって表されます。

## 例

```julia
# 特定の時間に測定されたデータ値をシミュレートします。
times = 1:100
values = sin.(0.0:0.1:100.0)

# 測定の不確実性が通常分布しているデバイスによってデータが測定されたと仮定します
# 標準偏差が変動する
σ_range = (0.1, 0.7)

uncertain_values = [UncertainValue(Normal, val, rand(Uniform(σ_range...))) 
    for val in values]

# 時間を記録するために使用された時計が不確実であると仮定しますが、
# 時間を通じて変わらない一様分布のノイズがあります。
uncertain_times = [UncertainValue(Uniform, t-0.1, t+0.1) for t in times]

# 時間-値データをペアにします。ベクターがコンストラクタに提供されると、
# 最初のものはインデックスとして解釈され、2番目のものは値として解釈されます。
data = UncertainIndexValueDataset(uncertain_times, uncertain_values)

# より安全なオプションは、最初に UncertainIndexDataset と 
# UncertainValueDataset に変換することです。そうすれば、インデックスと
# 値を誤って混同することはありません。
uidxs = UncertainIndexDataset(uncertain_times)
uvals = UncertainValueDataset(uncertain_values)

data = UncertainIndexValueDataset(uidxs, uvals)
```
