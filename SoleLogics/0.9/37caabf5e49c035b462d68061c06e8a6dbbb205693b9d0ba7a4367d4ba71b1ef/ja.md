```
struct BaseLogic{G<:AbstractGrammar,A<:AbstractAlgebra} <: AbstractLogic{G,A}
    grammar::G
    algebra::A
end
```

文法と代数に基づく基本的な論理であり、文法と代数の両方がインスタンス化されています。

関連情報としては、[`grammar`](@ref)、[`algebra`](@ref)、[`AbstractGrammar`](@ref)、[`AbstractAlgebra`](@ref)、[`AbstractLogic`](@ref)があります。
