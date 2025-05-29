```
discreterange(f, start, stop; length)
```

`maprange(...)`に似ていますが、`length`個のユニークな整数を返します。

# 例

1から100までの10個の対数間隔の値：

```julia
# 通常の浮動小数点 maprange
julia> maprange(log, 1, 100, length=10)
10-element FlexiMaps.MappedArray{Float64, 1, FlexiMaps.var"#12#13"{typeof(log), Int64, Int64, StepRangeLen{Float64, Base.TwicePrecision{Float64}, Base.TwicePrecision{Float64}, Int64}, Int64, Int64}, StepRangeLen{Float64, Base.TwicePrecision{Float64}, Base.TwicePrecision{Float64}, Int64}}:
   1.0
   1.6681005372000588
   2.7825594022071245
   4.641588833612779
   7.742636826811271
  12.915496650148844
  21.544346900318843
  35.93813663804628
  59.948425031894104
 100.0

# 整数の discreterange
julia> discreterange(log, 1, 100, length=10)
10-element Vector{Int64}:
   1
   2
   3
   5
   9
  14
  23
  38
  61
 100
```
