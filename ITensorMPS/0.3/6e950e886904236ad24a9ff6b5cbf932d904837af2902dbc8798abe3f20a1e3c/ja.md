```
apply(A::MPO, x::MPS; kwargs...)
```

`MPO` `A`を`MPS` `x`と収束させ、その後、結果のMPSのプライムレベルを0に戻します。

`replaceprime(contract(A, x; kwargs...), 2 => 1)`と同等です。

利用可能な引数の詳細については、[`contract`](@ref)を参照してください。
