```
collapse(::Val{N}, As::AxisArray...) -> AxisArray
collapse(::Val{N}, labels::Tuple, As::AxisArray...) -> AxisArray
collapse(::Val{N}, ::Type{NewArrayType}, As::AxisArray...) -> AxisArray
collapse(::Val{N}, ::Type{NewArrayType}, labels::Tuple, As::AxisArray...) -> AxisArray
```

Collapses `AxisArray`s with `N` equal leading axes into a single `AxisArray`. All additional axes in any of the arrays are collapsed into a single additional axis of type `Axis{:collapsed, CategoricalVector{Tuple}}`.

### Arguments

  * `::Val{N}`: the greatest common dimension to share between all input                   arrays. The remaining axes are collapsed. All `N` axes must be common                   to each input array, at the same dimension. Values from `0` up to the                   minimum number of dimensions across all input arrays are allowed.
  * `labels::Tuple`: (optional) an index for each array in `As` used as the leading element in                  the index tuples in the `:collapsed` axis. Defaults to `1:length(As)`.
  * `::Type{NewArrayType<:AbstractArray{_, N+1}}`: (optional) the desired underlying array                                                type for the returned `AxisArray`.
  * `As::AxisArray...`: `AxisArray`s to be collapsed together.

### Examples

```
julia> price_data = AxisArray(rand(10), Axis{:time}(Date(2016,01,01):Day(1):Date(2016,01,10)))
1-dimensional AxisArray{Float64,1,...} with axes:
    :time, 2016-01-01:1 day:2016-01-10
And data, a 10-element Array{Float64,1}:
 0.885014
 0.418562
 0.609344
 0.72221
 0.43656
 0.840304
 0.455337
 0.65954
 0.393801
 0.260207

julia> size_data = AxisArray(rand(10,2), Axis{:time}(Date(2016,01,01):Day(1):Date(2016,01,10)), Axis{:measure}([:area, :volume]))
2-dimensional AxisArray{Float64,2,...} with axes:
    :time, 2016-01-01:1 day:2016-01-10
    :measure, Symbol[:area, :volume]
And data, a 10×2 Array{Float64,2}:
 0.159434     0.456992
 0.344521     0.374623
 0.522077     0.313256
 0.994697     0.320953
 0.95104      0.900526
 0.921854     0.729311
 0.000922581  0.148822
 0.449128     0.761714
 0.650277     0.135061
 0.688773     0.513845

julia> collapsed = collapse(Val(1), (:price, :size), price_data, size_data)
2-dimensional AxisArray{Float64,2,...} with axes:
    :time, 2016-01-01:1 day:2016-01-10
    :collapsed, Tuple{Symbol,Vararg{Symbol,N} where N}[(:price,), (:size, :area), (:size, :volume)]
And data, a 10×3 Array{Float64,2}:
 0.885014  0.159434     0.456992
 0.418562  0.344521     0.374623
 0.609344  0.522077     0.313256
 0.72221   0.994697     0.320953
 0.43656   0.95104      0.900526
 0.840304  0.921854     0.729311
 0.455337  0.000922581  0.148822
 0.65954   0.449128     0.761714
 0.393801  0.650277     0.135061
 0.260207  0.688773     0.513845

julia> collapsed[Axis{:collapsed}(:size)] == size_data
true
```
