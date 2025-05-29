```
edgeroot(f, edge, M; kwargs...)
```

`edge` に沿った根を `Roots.find_zero` を呼び出して見つけます。`M` と `kwargs` は直接 `find_zero` に渡されます。

# 例

```jldoctest
julia> f(x) = 1 - sum(abs2, x); # 単位円

julia> BG = bisect(f, (0.0:1.0, 0.0:1.0); iterations=3);

julia> E = edges(BG)
8-element Vector{Tuple{Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 ((0.75, 0.0), (1.0, 0.0))
 ((0.75, 0.25), (1.0, 0.25))
 ((0.75, 0.5), (1.0, 0.5))
 ((0.75, 0.5), (0.75, 0.75))
 ((0.0, 0.75), (0.0, 1.0))
 ((0.25, 0.75), (0.25, 1.0))
 ((0.5, 0.75), (0.75, 0.75))
 ((0.5, 0.75), (0.5, 1.0))

julia> tracks = Roots.Tracks();

julia> root = edgeroot(f, E[3], Roots.ITP(); tracks)
(0.8660254037844387, 0.5)

julia> f(root)
0.0

julia> tracks
Results of univariate zero finding:

* Converged to: 0.8660254037844387
* Algorithm: Roots.ITP{Float64, Int64}(0.2, 2, 1)
* iterations: 7
* function evaluations ≈ 9
* stopped as f(x_n) = 0

Trace:
(a₀, b₀) = ( 0.75, 1 )
(a₁, b₁) = ( 0.75, 0.86964285714285705 )
(a₂, b₂) = ( 0.86290337975046705, 0.86964285714285705 )
(a₃, b₃) = ( 0.86290337975046705, 0.8660279692952968 )
(a₄, b₄) = ( 0.86602344653979335, 0.8660279692952968 )
(a₅, b₅) = ( 0.86602344653979335, 0.86602540378563075 )
(a₆, b₆) = ( 0.86602540378367243, 0.86602540378563075 )
(a₇, b₇) = ( 0.86602540378443871, 0.86602540378563075 )
```
