```julia
generate_starting_config(
    lattice::ActinRingsMC.Lattice,
    Nfil::Int64,
    Nsca::Int64,
    lf::Int64,
    overlap::Int64
) -> Vector{ActinRingsMC.Filament}

```

均一なオーバーラップを持つ開始構成を生成します。

足場フィラメントの数 Nsca と格子の数 lf は偶数でなければなりません。
