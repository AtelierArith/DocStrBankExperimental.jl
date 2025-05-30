```
apply(A::MPO, B::MPO; kwargs...)
```

`MPO` `A'` と `MPO` `B` を収束させ、その後、結果のMPOのプライムレベルを1と0のインデックスのペアを持つように戻します。

`replaceprime(contract(A', B; kwargs...), 2 => 1)` と同等です。

利用可能な引数の詳細については、[`contract`](@ref)を参照してください。
