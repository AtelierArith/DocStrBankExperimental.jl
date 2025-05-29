```
rr2([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

Calculates the squared radius to a reference pixel. In this case `CtrFT` is the center defined by the FFT convention. `ScaUnit` leaves the values unscaled. `offset` and `scale` can be either of `<:Ctr`, `<:Sca` respectively or simply tuples with the same shape as `size`. Look at `?Ctr` and `?Sca` for all options. `dims` is a keyword argument to specifiy over which dimensions the operation will effectively happen.

The arguments `offset`, and `scale` support list-mode, which means that supplying a tuple of tuples or a vector of tuples or a matrix causes the function to automatically generate a superposition of multiple versions of itself. The type of superposition is controlled by the `accumulator` argument. The relative strength of the individual superposition is controlled via the `weight` argument, which can be a tuple or vector. Have a look at the Voronoi-example below.

Note that this function is based on a `IndexFunArray` and therefore does not allocate the full memory needed to represent the array.

# Examples

```jldoctest
julia> rr2((4, 4))
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 8.0  5.0  4.0  5.0
 5.0  2.0  1.0  2.0
 4.0  1.0  0.0  1.0
 5.0  2.0  1.0  2.0
```

## Change Reference Position

```jldoctest
julia> rr2((3,3), offset=CtrCorner)
3×3 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 0.0  1.0  4.0
 1.0  2.0  5.0
 4.0  5.0  8.0

julia> rr2((4,4), offset=CtrFT)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 8.0  5.0  4.0  5.0
 5.0  2.0  1.0  2.0
 4.0  1.0  0.0  1.0
 5.0  2.0  1.0  2.0

julia> rr2((4,4), offset=CtrMid)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 4.5  2.5  2.5  4.5
 2.5  0.5  0.5  2.5
 2.5  0.5  0.5  2.5
 4.5  2.5  2.5  4.5

julia> rr2((4,4), offset=CtrEnd)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 18.0  13.0  10.0  9.0
 13.0   8.0   5.0  4.0
 10.0   5.0   2.0  1.0
  9.0   4.0   1.0  0.0

julia> rr2((3, 3), offset=(1, 1))
3×3 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}:
 0.0  1.0  4.0
 1.0  2.0  5.0
 4.0  5.0  8.0
```

## Change Scaling

```jldoctest
julia> rr((4,4), scale=ScaUnit)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 2.82843  2.23607  2.0  2.23607
 2.23607  1.41421  1.0  1.41421
 2.0      1.0      0.0  1.0
 2.23607  1.41421  1.0  1.41421

julia> rr((4,4), scale=ScaNorm)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.942809  0.745356  0.666667  0.745356
 0.745356  0.471405  0.333333  0.471405
 0.666667  0.333333  0.0       0.333333
 0.745356  0.471405  0.333333  0.471405

julia> rr((4,4), scale=ScaFT)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.707107  0.559017  0.5   0.559017
 0.559017  0.353553  0.25  0.353553
 0.5       0.25      0.0   0.25
 0.559017  0.353553  0.25  0.353553

julia> rr((4,4), scale=ScaFTEdge)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 1.41421  1.11803   1.0  1.11803
 1.11803  0.707107  0.5  0.707107
 1.0      0.5       0.0  0.5
 1.11803  0.707107  0.5  0.707107

julia> rr2(Int, (3, 3), offset=(1, 1), scale=(10, 10))
3×3 IndexFunArray{Int64, 2, IndexFunArrays.var"#4#5"{Int64, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}:
   0  100  400
 100  200  500
 400  500  800
```

## Application to selected dimensions

Note that the code below yields a 3D array but with a one-sized trailing dimension. This can then be used for broadcasting.

```jldoctest
julia> x = ones(5,6,5);

julia> y=rr2(selectsizes(x,(1,2)))
5×6×1 IndexFunArray{Float64, 3, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64, Float64}, Tuple{Int64, Int64, Int64}}}:
[:, :, 1] =
 13.0  8.0  5.0  4.0  5.0  8.0
 10.0  5.0  2.0  1.0  2.0  5.0
  9.0  4.0  1.0  0.0  1.0  4.0
 10.0  5.0  2.0  1.0  2.0  5.0
 13.0  8.0  5.0  4.0  5.0  8.0
```

Similarly you can also use dimensions 2 and 3 yielding an array of `size(y) == (1,6,5)`.  Note that the necessary modification to the `Base.size` function is currently provided by this package.

## Using List-Mode Arguments

The code below generates 160 Voronoi cells at random positions. The `accumulator` was set to  mimimum yielding in each pixel the square distance to the closest Voronoi center. See `gaussian` for another example of using list-mode arguments.

```jldoctest
julia> y = rr2((1000,1000),offset = (1000.0,1000.0) .* rand(2,160), accumulator=minimum);

```

---

```
rr2(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

This is a wrapper for  `rr2(eltype(arr), size(arr), scaling=scaling, offset=offset)`.
