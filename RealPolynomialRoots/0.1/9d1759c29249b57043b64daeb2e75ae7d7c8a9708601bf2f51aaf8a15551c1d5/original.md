```
ANewDsc(p; root_bound=(lowerbound(p), upperbound(p)), max_depth=96)
refine_interval(p, a, b, L)
refine_roots(st::State)
```

A method to find isolating intervals for the real roots of a square-free polynomial specified by the cofficients stored in `p`.

  * `p`: the polynomial coefficients, `[a₀, a₁, …, aₙ]`, of a **square-free** polynomial.
  * `root_bound`: a lower bound and upper bound for the real roots.

Returns a `State` instance which has components:

  * `Isol` holding the isolating intervals. Iteration over a `State` object will iterate over `Isol`.
  * `Unresolved` holding any unresolved intervals. The show method alerts the presence of any such intervals.

The algorithm has a random step included, which leads to small variations in the output.

Examples:

```
julia> using RealPolynomialRoots

julia> ps = [-1, 254, -16129, 0, 0, 0, 0, 1] # mignotte polynomial with two nearby roots
8-element Vector{Int64}:
     -1
    254
 -16129
      0
      0
      0
      0
      1

julia> st = ANewDsc(ps)
There were 3 isolating intervals found:
[3.5…, 7.25…]₅₃
[0.00787401594698…, 0.00787401779189…]₆₃
[0.00787401419348…, 0.00787401594698…]₆₃

julia> ps = [3628800, -10628640, 12753576, -8409500, 3416930, -902055, 157773, -18150, 1320, -55, 1]; # πᵢ₌₁¹⁰ (x-i)

julia> st = ANewDsc(ps)
There were 10 isolating intervals found:
[9.25…, 10.2…]₅₃
[8.5…, 9.25…]₅₃
[7.5…, 8.5…]₅₃
[6.5…, 7.5…]₅₃
[5.62…, 6.5…]₅₃
[4.88…, 5.62…]₅₃
[3.0…, 4.75…]₅₃
[2.19…, 3.0…]₅₃
[1.28…, 2.19…]₅₃
[-0.5…, 1.31…]₅₃

julia> ps =[ # from https://discourse.julialang.org/t/root-isolation-of-real-rooted-integer-polynomials/51421/1
                      942438915208811912419937422298363203125
                   164182217245953398816894035758761902846875
                  4584900574568933770264468813466870772155175
                 48995332393110515074735075708247882042540865
                266674183150777010544241114017741621823207005
                852443280934837985352088128423887894438557515
               1738546146302892245736990844587487000484756535
               2381558158813900978436742173305983349418813145
               2262003889258248241081177038309445610985409335
               1516025051068561122302699855213604175083575145
                720810987764796866354279087485114863858085005
                241341213302325116160821160849326697595681275
                 55563538585119205063994483187179167406616375
                  8363912237256094118085070946083688310200625
                   740493466743082745510080711751444519503125
                    29215606371473169285018060091249259296875];

julia> ANewDsc(ps)
There were 15 isolating intervals found:
[-0.01617…, 0.0531…]₂₅₆
[-0.08643…, -0.01617…]₂₅₆
[-0.2285…, -0.08643…]₂₅₆
[-0.3711…, -0.2285…]₂₅₆
[-0.6562…, -0.3672…]₂₅₆
[-0.9531…, -0.6562…]₂₅₆
[-1.234…, -0.9531…]₂₅₆
[-1.84…, -1.25…]₂₅₆
[-2.125…, -1.812…]₂₅₆
[-2.438…, -2.125…]₂₅₆
[-3.0…, -2.44…]₂₅₆
[-3.281…, -3.031…]₂₅₆
[-3.562…, -3.281…]₂₅₆
[-3.875…, -3.562…]₂₅₆
[-4.188…, -3.875…]₂₅₆
```

## Refinement

The `refine_interval` method can be used to refine an interval to have width smaller than $2^{-L}$ where `L` may be specified, but otherwise comes from the intervals precision.

Alternatively, a package like `Roots` could be used; e.g: `[find_zero(st, I) for I ∈ st]` (where `st` is a `State` object returned by `ANewDsc`). If refinement over `Float64` values is desired and appropriate given the root separation, then that call can be modified, as with `[find_zero(st, Float64.(I)) for I ∈ st]`. (This should produce roots with a sign change between `nextfloat` and `prevfloat`.)

## Comparisons

Don't judge the algorithm by its implementation here. This implementation is not as performant as it could be.

Comparing to some alternatives, we have that the functionality from Hecke.jl (`Hecke._roots`) is **much** better. (The last example is 33 ≈ 0.14s/0.0042 times faster)

However, compared to other alternatives this implementation could be seen as useful:

```
julia> x = variable(Polynomial);

julia> p = -1 + 254*x - 16129*x^2 + x^15;

julia> ANewDsc(coeffs(p))  # ≈ 0.05 seconds;
There were 3 isolating intervals found:
[0.75…, 4.25…]₅₃
[0.00787401574803149653139…, 0.00787401574803149972047…]₂₁₂
[0.0078740157480314937167…, 0.00787401574803149653139…]₂₁₂

julia> filter(isreal, roots(p)) # much faster, but misses two roots with imaginary part ~ 1e-10
1-element Array{Complex{Float64},1}:
 2.1057742291764914 + 0.0im

julia> filter(isreal, AMRVW.roots(Float64.(coeffs(p)))) # using AMRVW. Similarly misses two roots
1-element Array{Complex{Float64},1}:
 2.1057742291764407 + 0.0im

julia> filter(isreal, AMRVW.roots(BigFloat.(coeffs(p)))) # this works here
3-element Vector{Complex{BigFloat}}:
 0.007874015748031494751793842937491860399146218747427882112208862187156603046408902 + 0.0im
 0.007874015748031497374190409031015351762713667398750832139185145345899098824178322 + 0.0im
    2.105774229176482954331883383107195997983004314462374928263620342390986189650864 + 0.0im

julia> filter(isreal, PolynomialRoots.roots(coeffs(p))) # using PolynomialRoots. Misses 2.105?
2-element Array{Complex{Float64},1}:
   0.0078740158234482 + 0.0im
 0.007874015672614794 + 0.0im

julia> IntervalRootFinding.roots(x->p(x), IntervalArithmetic.Interval(0.0, 5.0)) # using IntervalRootFinding, IntervalArithmetic
8-element Array{Root{IntervalArithmetic.Interval{Float64}},1}:
 Root([2.10577, 2.10578], :unique)
 Root([0.00787418, 0.00787422], :unknown)
 Root([0.00787403, 0.00787409], :unknown)
[...]

julia> @syms x::real # using SymPy

julia> @time  rts = sympy.real_roots(p(x)); # correctly identifies 3.
  0.003896 seconds (518 allocations: 13.359 KiB)

julia> sympy.N(rts[2]) # takes a long time! (162s)
0.00787401574803150
```

The algorithm used is a partial implementation of one presented in:

*Computing Real Roots of Real Polynomials ... and now For Real!* by Alexander Kobel, Fabrice Rouillier, Michael Sagraloff [arXiv](https://arXiv.org/1605.00410); [DOI:](https://doi.org/10.1145/2930889.2930937).

and

*Computing real roots of real polynomials* Michael Sagraloff, Kurt Mehlhorn [DOI:](https://doi.org/10.1016/j.jsc.2015.03.004)

The algorithm relies on Descartes' rule of signs, which gives a bound on the number of positive real roots of a polynomial, `p(x)`. By considering the polynomial `p((ax+b)/(x+1))` (a mapping of `[a,b]` to `[0,∞)` a bound on the number of roots in `[a,b]` can be found. A simple bisection algorithm for a square-free polynomial would be to start with an interval large enough to contain all the real roots, then subdivide at the midpoint throwing out sub intervals which are found to have no root; saving intervals known to have 1 root, and repeating the subdivision otherwise. Issues with this are the need for many subdivisions when clusters of roots are present and the numeric issues that arise in computing the mapping.

The work of Sagaraloff, Melhorn, Kobel, and Rouillier improves this by introducing a Newton test and boundary test for rapidly decreasing the size of an interval when possible, and the ability to use finite precision arithmetic, instead of exact arithmetic, to compute the Descartes' bound, in addition to other algorithmic improvements (not all implemented here).

!!! note
    A square free polynomial can be found through `p/gcd(p, p')`, though in practice this calculation is numerically unstable.


!!! note
    This implementation is **much** slower than the `Hecke.roots` function provided through `arblib` in `Hecke.jl`, which itself says is not competitive with more specialized implementations, such as provided by the paper authors (http://anewdsc.mpi-inf.mpg.de/). There are several reasons: The `mobius_transform!` function is `𝑶(n²)`, and could be `𝑶(n⋅log(n))` with more effort; the polynomial evaluation in `admissiblepoint` could, similarly, be made more efficient; despite using tricks learned from the `MutableArithmetics.jl` package to reduce allocations with the `BigFloat` type, there are still *far* too many allocations as each time the precision is changed new (allocating) values must be created, as the old ones can't be modified in place (using `set_prec!` causes segfaults); the significant engineering speedups suggested by Kobel, Rouillier, and Sagraloff are not implemented; etc.

