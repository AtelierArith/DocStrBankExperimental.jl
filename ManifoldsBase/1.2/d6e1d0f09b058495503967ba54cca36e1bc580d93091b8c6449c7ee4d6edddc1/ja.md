```
CayleyRetraction <: AbstractRetractionMethod
```

ケイリー変換に基づく再tractionであり、[`PadeRetraction`](@ref)`{1}`を使用して実現されます。

!!! note "技術的注意"
    例えば、[`retract`](@ref)`(M, p, X, CayleyRetraction())`を呼び出してケイリー再tractionを実装する場合は、あなたの多様体`M`のために[`retract_cayley!`](@ref)`(M, q, p, X, t)`を定義してください。デフォルトでは、これらの関数は両方とも[`PadeRetraction`](@ref)`(1)`を呼び出すことにフォールバックします。

