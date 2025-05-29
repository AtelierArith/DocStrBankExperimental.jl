```
CayleyInverseRetraction <: AbstractInverseRetractionMethod
```

ケイリー変換に基づく再tractionであり、[`PadeRetraction`](@ref)`{1}`を使用して実現されます。

!!! note "技術的注意"
    逆ケイリー再tractionを実装するために、例えば[`inverse_retract`](@ref)`(M, p, q, CayleyInverseRetraction())`と呼び出すことになりますが、あなたの多様体`M`のために[`inverse_retract_cayley!`](@ref)`(M, X, p, q)`を定義してください。デフォルトでは、これらの関数は[`PadeInverseRetraction`](@ref)`(1)`を呼び出すことにフォールバックします。

