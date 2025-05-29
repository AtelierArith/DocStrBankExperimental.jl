`unipotent_character(W,l)` または `unichar(W,l)`

指定された `l` のユニポテントキャラクターを表すオブジェクトを構築します。これは、Coxeter群またはCoxeterコセットに関連付けられた代数群に対して指定された `W` に基づいています。 `l` には3つの可能性があります：整数の場合、`W` の `l`-th ユニポテントキャラクターが返されます。文字列の場合、名前が `l` である `W` のユニポテントキャラクターが返されます（名前は `charnames(UnipotentCharacters(W))` によって与えられます）。最後に、`l` は `W` のユニポテントキャラクターの数と同じ長さのリストであり、各ユニポテントキャラクターに与える係数を指定します。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> u=unichar(W,7)
[G₂]:<G₂[-1]>

julia> v=unichar(W,"G2[E3]")
[G₂]:<G₂[ζ₃]>

julia> w=unichar(W,[1,0,0,-1,0,0,2,0,0,1])
[G₂]:<φ₁‚₀>-<φ″₁‚₃>+2<G₂[-1]>+<G₂[ζ₃²]>

julia> unichar(W,fourier(UnipotentCharacters(W))[3,:])
[G₂]:2//3<φ′₁‚₃>-1//3<φ″₁‚₃>+1//3<φ₂‚₁>+1//3<G₂[1]>-1//3<G₂[ζ₃]>-1//3<G₂[ζ₃²]>
```

最後の行は、`W` の3番目のユニポテントキャラクターに関連付けられたほぼキャラクターを示しています。

ユニポテントキャラクターに対しては、いくつかの限られた算術が利用可能です：

```julia-repl
julia> coefficients(u) # したがって u==unichar(W,coefficients(u))
10-element Vector{Int64}:
 0
 0
 0
 0
 0
 0
 1
 0
 0
 0

julia> w-2u
[G₂]:<φ₁‚₀>-<φ″₁‚₃>+<G₂[ζ₃²]>

julia> w*w  # スカラー積
7

julia> degree(w)
Pol{Int64}: q⁵-q⁴-q³-q²+q+1
```
