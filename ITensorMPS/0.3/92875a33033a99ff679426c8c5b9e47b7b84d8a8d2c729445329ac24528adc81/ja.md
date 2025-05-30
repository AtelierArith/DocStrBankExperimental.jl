```
normalize(A::MPS; (lognorm!)=[])
normalize(A::MPO; (lognorm!)=[])
```

元のMPSまたはMPO `A` と同じでありながら `norm(A) ≈ 1` である新しいMPSまたはMPOを返します。

実際には、これは数値的オーバーフローを避けるために、直交中心の範囲内のテンソルに `lognorm(A)` を均等に分散させます。

[`normalize!`](@ref)、[`norm`](@ref)、[`lognorm`](@ref) も参照してください。
