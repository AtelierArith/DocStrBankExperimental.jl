```
Link
```

An abstract type whose subtypes refer to link functions.

GLM currently supports the following links: [`CauchitLink`](@ref), [`CloglogLink`](@ref), [`IdentityLink`](@ref), [`InverseLink`](@ref), [`InverseSquareLink`](@ref), [`LogitLink`](@ref), [`LogLink`](@ref), [`NegativeBinomialLink`](@ref), [`PowerLink`](@ref), [`ProbitLink`](@ref), [`SqrtLink`](@ref).

Subtypes of `Link` are required to implement methods for [`GLM.linkfun`](@ref), [`GLM.linkinv`](@ref), [`GLM.mueta`](@ref), and [`GLM.inverselink`](@ref).
