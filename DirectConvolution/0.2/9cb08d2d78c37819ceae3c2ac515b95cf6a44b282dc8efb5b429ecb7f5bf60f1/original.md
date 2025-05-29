```
function SG_Filter(T::DataType=Float64;halfWidth::Int=5,degree::Int=2)
```

Creates a `SG_Filter` structure used to store Savitzky-Golay filters.

  * filter length is 2*`halfWidth`+1
  * polynomial degree is `degree`, which defines `maxDerivativeOrder`

You can apply these filters using the 

  * `apply_SG_filter`
  * `apply_SG_filter2D`

functions.

Example:

```jldoctest
julia> sg = SG_Filter(halfWidth=5,degree=3);


julia> maxDerivativeOrder(sg)
3

julia> length(sg)
11

julia> filter(sg,derivativeOrder=2)
Filter(r=-5:5,c=[0.03497, 0.01399, -0.002331, -0.01399, -0.02098, -0.02331, -0.02098, -0.01399, -0.002331, 0.01399, 0.03497])

```
