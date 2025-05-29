```
struct BooleanAlgebra <: AbstractAlgebra{Bool} end
```

A [Boolean algebra](https://en.wikipedia.org/wiki/Boolean_algebra)、値TOP（*真*を表す）とBOT（*偽*を表す）で定義されます。この代数において、基本演算子である否定、結合、選言（スタイライズされた記号は ¬、∧、∨）は、それぞれ`true`と`false`の整数キャストの補集合、最小値、最大値として定義できます。

また、[`Truth`](@ref)も参照してください。
