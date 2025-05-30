```
all_spin_pols(process::AbstractProcessDefinition)
```

この関数は、プロセスの[`spin_pols`](@ref)によって許可されるすべての完全に確定したスピンと偏光の組み合わせを生成するイテレータを返します。返される各要素は、プロセス自身のスピンと偏光の順序で、入射スピンと偏光および出射スピンと偏光のタプルです。

これは、確定したスピンと偏光、[`AllSpin`](@ref)、[`AllPolarization`](@ref)、および同期されたバージョン[`SyncedPolarization`](@ref)と[`SyncedSpin`](@ref)と一緒に機能します。

```julia
julia> using QEDbase; using QEDcore; using QEDprocesses;

julia> proc = ScatteringProcess((Photon(), Photon(), Photon(), Electron()), (Photon(), Electron()), (SyncedPolarization(1), SyncedPolarization(2), SyncedPolarization(1), SpinUp()), (SyncedPolarization(2), AllSpin()))
generic QED process
    incoming: photon (synced polarization 1), photon (synced polarization 2), photon (synced polarization 1), electron (spin up)
    outgoing: photon (synced polarization 2), electron (all spins)


julia> for sp_combo in spin_pols_iter(proc) println(sp_combo) end
((x-polarized, x-polarized, x-polarized, spin up), (x-polarized, spin up))
((y-polarized, x-polarized, y-polarized, spin up), (x-polarized, spin up))
((x-polarized, y-polarized, x-polarized, spin up), (y-polarized, spin up))
((y-polarized, y-polarized, y-polarized, spin up), (y-polarized, spin up))
((x-polarized, x-polarized, x-polarized, spin up), (x-polarized, spin down))
((y-polarized, x-polarized, y-polarized, spin up), (x-polarized, spin down))
((x-polarized, y-polarized, x-polarized, spin up), (y-polarized, spin down))
((y-polarized, y-polarized, y-polarized, spin up), (y-polarized, spin down))

julia> length(spin_pols_iter(proc))
8
```
