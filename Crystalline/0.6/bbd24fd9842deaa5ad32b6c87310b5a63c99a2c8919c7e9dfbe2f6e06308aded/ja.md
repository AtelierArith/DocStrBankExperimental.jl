```
Reality <: Enum{Int8}
```

インスタンスを持つ列挙型

```
REAL = 1
PSEUDOREAL = -1
COMPLEX = 0
```

[`reality(::AbstractIrrep)`](@ref) と [`calc_reality`](@ref) の戻り値は `Reality` のインスタンスです。irrep の現実型は、[`realify`](@ref) を介して「物理的に実在する」irrep（co-rep）を構築する際に関連しています。
