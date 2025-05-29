```
find_zeros(f, a, [b]; [no_pts=12, k=8, naive=false, xatol, xrtol, atol, rtol])
```

Search for zeros of `f` in the interval `[a,b]` with an heuristic algorithm.

  * `f`: a function or callable object
  * `a`, `b`:  If `b` is specified, the interval $[a,b]$ is used. If only `a` is specified, it is passed to `extrema` to define the interval to search over.   It is assumed that neither endpoint is a zero.

Returns a vector of zeros in sorted order, possibly empty.

# Extended help

# Examples

```jldoctest find_zeros
julia> using Roots

julia> find_zeros(x -> exp(x) - x^4, -5, 20)        # a few well-spaced zeros
3-element Vector{Float64}:
 -0.8155534188089606
  1.4296118247255556
  8.613169456441398

julia> find_zeros(x -> sin(x^2) + cos(x)^2, 0, 2pi)  # many zeros
12-element Vector{Float64}:
 1.78518032659534
 2.391345462376604
 3.2852368649448853
 3.3625557095737544
 4.016412952618305
 4.325091924521049
 4.68952781386834
 5.00494459113514
 5.35145266881871
 5.552319796014526
 5.974560835055425
 6.039177477770888

julia> find_zeros(x -> cos(x) + cos(2x), (0, 4pi))    # mix of simple, non-simple zeros
6-element Vector{Float64}:
  1.0471975511965976
  3.141592653589943
  5.235987755982988
  7.330382858376184
  9.424777960769228
 11.519173063162574

julia> f(x) = (x-0.5) * (x-0.5001) * (x-1)          # nearby zeros
f (generic function with 1 method)

julia> find_zeros(f, 0, 2)
3-element Vector{Float64}:
 0.5
 0.5001
 1.0

julia> f(x) = (x-0.5) * (x-0.5001) * (x-4) * (x-4.001) * (x-4.2)
f (generic function with 1 method)

julia> find_zeros(f, 0, 10)
3-element Vector{Float64}:
 0.5
 0.5001
 4.2

julia> f(x) = (x-0.5)^2 * (x-0.5001)^3 * (x-4) * (x-4.001) * (x-4.2)^2  # hard to identify
f (generic function with 1 method)

julia> find_zeros(f, 0, 10, no_pts=21)                # too hard for default
5-element Vector{Float64}:
 0.49999999999999994
 0.5001
 4.0
 4.001
 4.200000000000001
```

!!! note
    Some cases where the number of zeros may be underreported:

      * if the initial interval, `(a,b)`, is too wide
      * if there are zeros  that are very nearby
      * the function is flat, e.g., `x->0`.


---

The basic algorithm checks for zeros among the endpoints, and then divides the interval `(a,b)` into `no_pts-1` subintervals and then proceeds to look for zeros through bisection or a derivative-free method.  As checking for a bracketing interval is relatively cheap and bisection is guaranteed to converge, each interval has `k` pairs of intermediate points checked for a bracket.

If any zeros are found, the algorithm uses these to partition `(a,b)` into subintervals. Each subinterval is shrunk so that the endpoints are not zeros and the process is repeated on the subinterval. If the initial interval is too large, then the naive scanning for zeros may be fruitless and no zeros will be reported. If there are nearby zeros, the shrinking of the interval may jump over them, though as seen in the examples, nearby roots can be identified correctly, though for really nearby points, or very flat functions, it may help to increase `no_pts`.

The tolerances are used to shrink the intervals, but not to find zeros within a search. For searches, bisection is guaranteed to converge with no specified tolerance. For the derivative free search, a modification of the `Order0` method is used, which at worst case compares `|f(x)| <= 8*eps(x)` to identify a zero. The algorithm might identify more than one value for a zero, due to floating point approximations. If a potential pair of zeros satisfy `isapprox(a,b,atol=sqrt(xatol), rtol=sqrt(xrtol))` then they are consolidated.

The algorithm can make many function calls. When zeros are found in an interval, the naive search is carried out on each subinterval. To cut down on function calls, though with some increased chance of missing some zeros, the adaptive nature can be skipped with the argument `naive=true` or the number of points stepped down.

The algorithm is derived from one in a [PR](https://github.com/JuliaMath/Roots.jl/pull/113) by @djsegal.

!!! note
    The `IntervalRootFinding` package provides a rigorous alternative to this heuristic one. That package uses interval arithmetic, so can compute bounds on the size of the image of an interval under `f`. If this image includes `0`, then it can look for the zero. Bisection, on the other hand, only will look for a zero if the two endpoints have different signs, a much more rigid condition for a potential zero.


!!! note "`IntervalRootFinding` extension"
    As of version `1.9` an extension is provided so that when the `IntervalRootFinding` package is loaded, the `find_zeros` function will call `IntervalRootFinding.roots` to find the isolating brackets and `find_zero` to find the roots, when possible, **if** the interval is specified as an `Interval` object, as created by `-1..1`, say.


For example, this function (due to `@truculentmath`) is particularly tricky, as it is positive at every floating point number, but has two zeros (the vertical asymptote at `15//11` is only negative within adjacent floating point values):

```
julia> using IntervalArithmetic, IntervalRootFinding, Roots

julia> g(x) = x^2 + 1 +log(abs( 11*x-15 ))/99
g (generic function with 1 method)

julia> find_zeros(g, -3, 3)
Float64[]

julia> IntervalRootFinding.roots(g, -3..3, IntervalRootFinding.Bisection)
1-element Vector{Root{Interval{Float64}}}:
 Root([1.36363, 1.36364], :unknown)
```

A less extreme usage might be the following, where `unique` indicates Bisection could be useful and indeed `find_zeros` will identify these values:

```
julia> g(x) = exp(x) - x^5
g (generic function with 1 method)

julia> rts = IntervalRootFinding.roots(g, -20..20)
2-element Vector{Root{Interval{Float64}}}:
 Root([12.7132, 12.7133], :unique)
 Root([1.29585, 1.29586], :unique)

julia> find_zeros(g, -20, 20)
2-element Vector{Float64}:
  1.2958555090953687
 12.713206788867632
```
