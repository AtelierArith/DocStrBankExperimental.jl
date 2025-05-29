```
apply!([α=1,] [P=Direct,] A::Mapping, x, [scratch=false,] [β=0,] y) -> y
```

overwrites `y` with `α*P(A)⋅x + β*y` where `P ∈ Operations` can be `Direct`, `Adjoint`, `Inverse` and/or `InverseAdjoint` to indicate which variant of the mapping `A` to apply. The convention is that the prior contents of `y` is not used at all if `β = 0` so `y` can be directly used to store the result even though it is not initialized. The `scratch` optional argument indicates whether the input `x` is no longer needed by the caller and can thus be used as a scratch array. Having `scratch = true` or `β = 0` may be exploited by the specific implementation of the `apply!` method for the mapping type to avoid allocating temporary workspace(s).

The `apply!` method can be seen as a generalization of the `LinearAlgebra.mul!` method.

The order of arguments can be changed and the same result as above is obtained with:

```
apply!([β=0,] y, [α=1,] [P=Direct,] A::Mapping, x, scratch=false) -> y
```

The result `y` may have been allocated by:

```
y = vcreate(P, A, x, scratch=false)
```

or by:

```
y = vcreate(A, x, scratch=false)
```

if `P` is not specified.

Mapping sub-types only need to extend `vcreate` and `apply!` with the specific signatures:

```
vcreate(::Type{P}, A::M, x, scratch::Bool=false) -> y
apply!(α::Number, ::Type{P}, A::M, x, scratch::Bool, β::Number, y) -> y
```

for any supported operation `P` and where `M` is the type of the mapping. Of course, the types of arguments `x` and `y` may be specified as well.

Optionally, the method with signature:

```
apply(::Type{P}, A::M, x, scratch::Bool=false) -> y
```

may also be extended to improve the default implementation which is:

```
apply(P::Type{<:Operations}, A::Mapping, x, scratch::Bool=false) =
    apply!(1, P, A, x, scratch, 0, vcreate(P, A, x, scratch))
```

See also: [`Mapping`](@ref), [`apply`](@ref), [`vcreate`](@ref).
