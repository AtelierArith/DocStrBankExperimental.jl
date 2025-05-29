```
iA = IntegralArray([buffer,] A)
```

Construct the integral array of the input array `A`. If buffer of the same shape as `A` is provided, then this is a non-allocating version.

The integral array is calculated by assigning to each cell the sum of all cells above it and to its left, i.e. the rectangle from origin point to the pixel position. For example, in 1-D case, `iA[i] = sum(A[1:i])` if the vector `A`'s origin is 1.

```jldoctest; setup=:(using IntegralArrays)
julia> A = collect(reshape(1:25, 5, 5))
5×5 Matrix{Int64}:
 1   6  11  16  21
 2   7  12  17  22
 3   8  13  18  23
 4   9  14  19  24
 5  10  15  20  25

julia> iA = IntegralArray(A)
5×5 IntegralArray{Int64, 2, Matrix{Int64}}:
  1   7   18   34   55
  3  16   39   72  115
  6  27   63  114  180
 10  40   90  160  250
 15  55  120  210  325

julia> iA[3, 3] == sum(A[1:3, 1:3])
true

julia> iA[3..5, 3..5] == sum(A[3:5, 3:5])
true

julia> IntegralArray(A, A); # in-place modifying A itself

julia> A
5×5 Matrix{Int64}:
  1   7   18   34   55
  3  16   39   72  115
  6  27   63  114  180
 10  40   90  160  250
 15  55  120  210  325
```

The closed interval `a..b` is used to support the integral array `iX` with a different indexing semantic; `iX[a:b]` gives a subarray of `iX`, while `iX[a..b]` calculates the sum of original array `X` over region `a:b`. `a ± σ` (can be typed by `\pm<tab>`) is a convenient constructor of the closed interval `a-σ..a+σ`.

When one needs to compute the sum/average of all blocks extracted from an image, pre-building the integral array usually provides a more efficient computation.

```julia
using BenchmarkTools, IntegralArrays

# simplified 3x3 mean filter; only for demo purpose
function mean_filter_naive!(out, X)
    Δ = CartesianIndex(1, 1)
    for i in CartesianIndex(2, 2):CartesianIndex(size(X).-1)
        block = @view X[i-Δ: i+Δ]
        out[i] = mean(block)
    end
    return out
end
function mean_filter_integral!(out, X)
    iX = IntegralArray(X)
    for i in CartesianIndex(2, 2):CartesianIndex(size(X).-1)
        x, y = i.I
        out[i] = iX[x±1, y±1]/9
    end
    return out
end

X = Float32.(rand(1:5, 64, 64));
m1 = copy(X);
m2 = copy(X);

@btime mean_filter_naive!($m1, $X); # 65.078 μs (0 allocations: 0 bytes)
@btime mean_filter_integral!($m2, $X); # 12.161 μs (4 allocations: 16.17 KiB)
m1 == m2 # true
```
