```
vnorm1([T,] v)
```

yields the L1 norm of `v`, that is the sum of the absolute values of its elements.  The floating point type of the result can be imposed by optional argument `T`.  For a complex valued argument, the result is the sum of the absolute values of the real part and of the imaginary part of the elements (like BLAS `asum`).

See also [`vnorm2`](@ref) and [`vnorminf`](@ref).
