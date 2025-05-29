```
RationalGenerator(n)
RationalGenerator()
```

Create an iterator that produces positive rational numbers without repetition. 

  * `RationalGenerator(n)` creates all rational numbers of the form `a//b` where `gcd(a,b) = 1` and `a+b ≤ n`.
  * `RationalGenerator()` creates all rational numbers. Invoking `RationalGenerator` with a negative argument has the same effect.

Note: `RatGen` may be used an abbrevation in place of `RationalGenerator`.

Example:

```
julia> collect(RatGen(5))'
1×9 adjoint(::Vector{Rational{Int64}}) with eltype Rational{Int64}:
 1//1  1//2  2//1  1//3  3//1  1//4  2//3  3//2  4//1
```
