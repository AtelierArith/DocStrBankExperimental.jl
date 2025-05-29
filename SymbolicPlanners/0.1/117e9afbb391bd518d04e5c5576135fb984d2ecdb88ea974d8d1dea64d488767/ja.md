```julia
abstract type Specification
```

問題仕様のための抽象型で、目標述語、行動コスト、報酬関数、および計画のための他の望ましい基準を定義できます [`Solution`](@ref)s。
