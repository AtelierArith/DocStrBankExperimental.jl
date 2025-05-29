```
normalize!(A::MPS; (lognorm!)=[])
normalize!(A::MPO; (lognorm!)=[])

MPSまたはMPO `A`をインプレースで変更して、`norm(A) ≈ 1`となるようにします。これは、直交中心内のテンソルのデータを修正します。

実際には、これは`lognorm(A)`を直交中心の範囲内のテンソルに均等に分配し、発散するノルムの場合の数値的オーバーフローを回避します。

入力MPSまたはMPOのノルムが0の場合、正規化は定義されていません。この場合、元のMPSまたはMPOをそのまま返します。このケースを次のように確認できます：

```

julia s = siteinds("S=1/2", 4) ψ = 0 * random*mps(s) lognorm*ψ = [] normalize!(ψ; (lognorm!)=lognorm*ψ) lognorm*ψ[1] == -Inf # 無限大のノルムがありました

```

[`normalize`](@ref)、[`norm`](@ref)、[`lognorm`](@ref)も参照してください。
```
