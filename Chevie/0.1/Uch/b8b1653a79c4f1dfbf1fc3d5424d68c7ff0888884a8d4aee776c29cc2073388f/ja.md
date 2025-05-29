`lusztig_induce(W,u)`

`u` はコクセターコセット `W` の部分コセットのユニポテントキャラクターである必要があります。これは、`W` に付随する代数群 `𝐆` のレヴィ `𝐋` のユニポテントキャラクター `λ` を表します。このプログラムは、ルスティグ誘導 $R_𝐋^𝐆(λ)$ を返します。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> WF=spets(W)
G₂

julia> T=subspets(WF,Int[],W(1))
G₂₍₎=Φ₁Φ₂

julia> u=unichar(T,1)
[G₂₍₎=Φ₁Φ₂]:<Id>

julia> lusztig_induce(WF,u)
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>

julia> dlchar(W,W(1))
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>
```
