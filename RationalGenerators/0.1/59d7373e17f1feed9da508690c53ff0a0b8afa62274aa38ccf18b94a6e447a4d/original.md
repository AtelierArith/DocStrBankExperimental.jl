```
SmallRationalGenerator()
SmallRationalGenerator(last_denominator)
```

Create an iterator that gives rational numbers in the interval `(0,1]` without  repetition. 

If `last_denominator` is specified, only produce rationals with  that denominator or smaller (a negative argument has the same effect).

Example:

```
julia> collect(SmallRatGen(5))'
1×10 adjoint(::Vector{Rational{Int64}}) with eltype Rational{Int64}:
 1//1  1//2  1//3  2//3  1//4  3//4  1//5  2//5  3//5  4//5
```
