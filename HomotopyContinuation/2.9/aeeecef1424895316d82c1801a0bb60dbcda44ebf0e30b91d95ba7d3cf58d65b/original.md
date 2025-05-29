```
Tracker(H::AbstractHomotopy;
        options = TrackerOptions(),
        weighted_norm_options = WeightedNormOptions())
```

Construct a tracker for the given homotopy `H`. The algorithm computes along the path $x(t)$ the local derivatives up to order 4. For `options` see also [`TrackerOptions`](@ref). The algorithm uses as a weighted infinity norm to measure distances. See also [`WeightedNorm`](@ref).

[^Tim20]: Timme, S. "Mixed Precision Path Tracking for Polynomial Homotopy Continuation". arXiv:1902.02968 (2020)

## Example

We want to solve the system

```julia
@var x y t
F = System([x^2 + y^2 - 3, 2x^2 + 0.5x*y + 3y^2 - 2])
```

using a total degree homotopy and `Tracker`.

```julia
# construct start system and homotopy
G = System(im * [x^2 - 1, y^2 - 1])
H = StraightLineHomotopy(G, F)
start_solutions = [[1,1], [-1,1], [1,-1], [-1,-1]]
# construct tracker
tracker = Tracker(H)
# track each start solution separetely
results = track.(tracker, start_solutions)
println("# successfull: ", count(is_success, results))
```

We see that we tracked all 4 paths successfully.

```
# successfull: 4
```
