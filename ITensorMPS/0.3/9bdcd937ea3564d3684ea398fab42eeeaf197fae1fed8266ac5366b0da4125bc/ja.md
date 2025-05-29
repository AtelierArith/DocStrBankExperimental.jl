```
apply(A::MPO, B::MPO; kwargs...)
```

`MPO` `A'` を `MPO` `B` と収束させ、その後、結果の `MPO` のプライムレベルを1と0のインデックスのペアを持つように戻します。

`replaceprime(contract(A', B; kwargs...), 2 => 1)` と同等です。

利用可能な引数の詳細については、[`contract`](@ref) を参照してください。
