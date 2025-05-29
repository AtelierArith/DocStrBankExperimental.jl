An `a = Accumulator(v::AbstractVector; op=+, init=zero)` works as a replacement for `v` with extra tracking computation, such as `sum`. See also `CumSum` and `Cavity`

```
julia> a = Accumulator([1:10;])
10-element Accumulator{Int64, +, zero}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10

julia> sum(a)
55

julia> a[1]=0
0

julia> sum(a)
54

```
