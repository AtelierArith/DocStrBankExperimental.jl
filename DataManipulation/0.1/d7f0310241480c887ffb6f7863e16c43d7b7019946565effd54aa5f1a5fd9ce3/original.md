```
discreterange(f, start, stop; length)
```

Similar to `maprange(...)`, but return `length` unique integers.

# Example

10 log-spaced values from 1 to 100:

```julia
# regular floating-point maprange
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

# discreterange of integers
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
