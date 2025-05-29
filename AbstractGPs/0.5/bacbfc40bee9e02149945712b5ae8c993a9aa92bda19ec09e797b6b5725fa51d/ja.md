```
logpdf(f::FiniteGP, y::AbstractVecOrMat{<:Real})
```

`f`の下での`y`のlogpdfは、`y`がAbstractVectorの場合です。`y`がMatrixの場合は、`y`の各列のlogpdfです。

```jldoctest
julia> f = GP(Matern32Kernel());

julia> x = randn(11);

julia> y = rand(f(x));

julia> logpdf(f(x), y) isa Real
true

julia> Y = rand(f(x), 3);

julia> logpdf(f(x), Y) isa AbstractVector{<:Real}
true
```
