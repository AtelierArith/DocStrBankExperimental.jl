```
find_threshold(data::AbstractArray, f::AbstractThresholdAlgorithm; nbins)
find_threshold(histogram::AbstractArray, edges::AbstractArray, f::AbstractThresholdAlgorithm)
```

`data`内の適切な閾値を、`nbins`を使用してヒストグラムを構築する際にアルゴリズム`f`を用いて見つけます。生の`data`を指定する代わりに、ヒストグラムとそれに伴うエッジを直接指定することができます。

# 出力

データを2つの部分に分割するために使用できる閾値を表す実数。

# 例

単にアルゴリズムを`find_threshold`に渡すだけです：

```julia
using TestImages, HistogramThreshold
img = testimage("cameraman")
t = find_threshold(img, f ; nbins = 64)
```

```julia
using StatsBase, HistogramThreshold
data = vcat(ones(50,), zeros(50,))
h = fit(Histogram, data)
t = find_threshold(data, f ; nbins = 2)
```
