`lusztig_restrict(R,u)`

`u` は、`R` が部分コセットである親コクセターコセット `W` のユニポテントキャラクターである必要があります。これは、`W` に付随する代数群 `𝐆` のユニポテントキャラクター `γ` を表し、`R` はレヴィ部分群 `L` を表します。このプログラムは、ルスティグ制限 $*R_𝐋^𝐆(γ)$ を返します。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> WF=spets(W)
G₂

julia> T=subspets(WF,Int[],W(1))
G₂₍₎=Φ₁Φ₂

julia> u=dlchar(W,W(1))
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>

julia> lusztig_restrict(T,u)
[G₂₍₎=Φ₁Φ₂]:4<Id>

julia> T=subspets(WF,Int[],W(2))
G₂₍₎=Φ₁Φ₂

julia> lusztig_restrict(T,u)
[G₂₍₎=Φ₁Φ₂]:0
```
