```
castDef(grid::CamiDiff.Grid{T}, atom::Atom, spinorbit::Spinorbit, codata::Codata [; pos=nothing, [scr=nothing[, msg=false]]) where T <: Real
```

[`Def`](@ref) オブジェクトを [`CamiDiff.Grid`](@extref) オブジェクトとオブジェクトの原子特性で作成します [`Atom`](@ref) と [`Orbit`](@ref)。オプション: scr（スクリーニング配列を供給）

#### 例:

```
julia> codata = castCodata(2018)
julia> atom = castAtom(Z=1, A=1, Q=0);
julia> orbit = castOrbit(n=7, ℓ=2);
julia> grid = autoGrid(atom, orbit, Float64);

julia> castDef(grid, atom, orbit, codata, msg=true);
水素 7d のために 400 ポイントの指数グリッド上に Def が作成されました
```
