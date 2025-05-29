```
リンク
```

リンク関数を参照する抽象型。

GLMは現在、次のリンクをサポートしています: [`CauchitLink`](@ref), [`CloglogLink`](@ref), [`IdentityLink`](@ref), [`InverseLink`](@ref), [`InverseSquareLink`](@ref), [`LogitLink`](@ref), [`LogLink`](@ref), [`NegativeBinomialLink`](@ref), [`PowerLink`](@ref), [`ProbitLink`](@ref), [`SqrtLink`](@ref)。

`Link`のサブタイプは、[`GLM.linkfun`](@ref), [`GLM.linkinv`](@ref), [`GLM.mueta`](@ref), および[`GLM.inverselink`](@ref)のメソッドを実装する必要があります。
