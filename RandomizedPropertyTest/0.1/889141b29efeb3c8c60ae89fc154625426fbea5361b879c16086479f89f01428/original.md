```
@quickcheck [n=nexpr] expr (vartuple :: T) [...]
```

Check whether the property expressed by `expr` holds for variables `vartuple...` of type `T`. Multiple such variable declarations may be given. Returns `false` if a counterexample was found, `true` otherwise. It should be noted that a result of `true` does not constitute proof of the property.

`nexpr` is the number of pseudorandom inputs used to examine the veracity of the property. It has no effect on special cases, which are always checked. To check only special cases, you may set `nexpr` to zero.

For reproducibility of counterexamples, inputs are chosen pseudorandomly with a fixed seed. Instead of running `@quickcheck` multiple times to be more certain of the property you wish to verify, run it once with a larger `n`.

To use `@quickcheck` with custom data types or custom distributions of builtin datatypes, see `generate` and `specialcases`. Some data types for custom distributions (e.g. `Range{T,a,b}`) are predefined in this module.

## Examples

Check the associativity of `+` for Ints:

```jldoctest
julia> @quickcheck (a+b == b+a) (a :: Int) (b :: Int)
true
```

The same test with alternative syntax and a larger number of tests:

```jldoctest
julia> @quickcheck n=10^6 (a+b == b+a) ((a, b) :: Int)
true
```

On the other hand, a test of the associativity of double-precision floats fails, even if only finite values are allowed (no `NaN`, ±`Inf`):

```jldoctest
julia> @quickcheck (a+(b+c) == (a+b)+c || !all(isfinite, (a,b,c))) ((a,b,c) :: Float64)
┌ Warning: Property `a + (b + c) == (a + b) + c || (any(isnan, (a, b, c)) || any(isinf, (a, b, c)))` does not hold for (a = 0.3333333333333333, b = 1.0, c = 1.0).
└ @ RandomizedPropertyTest ~/store/zeug/public/RandomizedPropertyTest/src/RandomizedPropertyTest.jl:119
false
```

Test an addition theorem of `sin` over one period:

```jldoctest
julia> @quickcheck (sin(α - β) ≈ sin(α) * cos(β) - cos(α) * sin(β)) ((α, β) :: Range{Float64, 0, 2π})
true
```
