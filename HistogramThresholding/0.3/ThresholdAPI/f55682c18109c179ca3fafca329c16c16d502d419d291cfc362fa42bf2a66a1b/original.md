```
find_threshold(data::AbstractArray, f::AbstractThresholdAlgorithm; nbins)
find_threshold(histogram::AbstractArray, edges::AbstractArray, f::AbstractThresholdAlgorithm)
```

Find a suitable threshold in `data` using algorithm `f` upon constructing a histogram with `nbins`. Instead of specifing the raw `data`, you can specify a histogram and accompanying edges directly. 

# Output

A real number representing a threshold that can be used to split data into two parts. 

# Examples

Just simply pass an algorithm to `find_threshold`:

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
