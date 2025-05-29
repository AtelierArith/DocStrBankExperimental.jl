Compute the `n-th` degree Chebyshev polynomial of first and second kind and its derivatives

  * `chebyshev(x, n)` Chebyshev polynomial of the first kind
  * `chebyshev2(x, n)` Chebyshev polynomial of the second kind
  * `dchebyshev(x, n)` Derivative of Chebyshev polynomial of the first kind
  * `dchebyshev2(x, n)` Derivative of Chebyshev polynomial of the second kind

There are also functions that compute the zeros of Chebyshev polynomials:

  * `chebyshev_zeros`
  * `chebyshev2_zeros`
  * `chebyshev_zeros!`
  * `chebyshev2_zeros!`

# Example

```julia-repl

julia> chebyshev(0.3, 5)
0.9988800000000001

julia> chebyshev2(0.3, 5)
1.01376

julia> dchebyshev(0.3, 5)
0.24800000000000044

julia> dchebyshev2(0.3, 5)
-1.3439999999999992

julia> chebyshev_zeros(5)
5-element Array{Float64,1}:
 -0.9510565162951535
 -0.5877852522924731
 -0.0
  0.587785252292473
  0.9510565162951536

julia> chebyshev_zeros(5, BigFloat)
5-element Array{BigFloat,1}:
 -0.9510565162951535721164393333793821434056986341257502224473056444301531700851959
 -0.5877852522924731291687059546390727685976524376431459910722724807572784741623414
 -0.0
  0.5877852522924731291687059546390727685976524376431459910722724807572784741623414
  0.9510565162951535721164393333793821434056986341257502224473056444301531700851873
```
