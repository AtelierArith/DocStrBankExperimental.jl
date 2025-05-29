OUTSCH!(Z::Vector{Complex{T}}, E::T, grid::CamiDiff.Grid{T}, def::Def{T}, adams::Adams{T}) where T<:Real

放射波動方程式の最初の $k$ ポイントの *外向き* 積分のための Ansatz 解で、ここで $k$ は Adams-Moulton の次数です。角運動量 `0 ≤ ℓ ≤ 5` の場合、Walter Johnson Ansatz が使用されます; $ℓ > 5$ の場合、 Ansatz はエネルギー `E` に対する WKB 解に基づいており、内側の古典的な転回点よりも *はるかに遠い* 距離でのものです - ictp)

#### 例:

```
Ecal, grid, def, adams = demo_hydrogen(n=1, ℓ=0)
Z = OUTSCH(Ecal, grid, def, adams.σ)
println("\nZ: wavefunction の標準 Ansatz (n < Na=$(def.pos.Na)))")
    Orbital: 1s
        主量子数: n = 1
        放射量子数: n′ = 0 (放射波動関数のノード数)
        関与電子の軌道角運動量: ℓ = 0
    CamiDiff.Grid が作成されました: 指数関数, Float64, Rmax = 63.0 a.u., N = 100, h = 0.1, r0 = 0.00286033
    水素 1s のための Def が指数関数グリッド上に作成されました

    Z: wavefunction の標準 Ansatz (n < Na=8))

Ecal, grid, def, adams = demo_hydrogen(n=10, ℓ=5)
Z = OUTSCH(Ecal, grid, def, adams.σ);
println("\nZ: wavefunction の WKB Ansatz (n < Na=$(def.pos.Na)))")
    Orbital: 10h
        主量子数: n = 10
        放射量子数: n′ = 4 (放射波動関数のノード数)
        関与電子の軌道角運動量: ℓ = 5
    CamiDiff.Grid が作成されました: 指数関数, Float64, Rmax = 360.0 a.u., N = 550, h = 0.0181818, r0 = 0.0163447
    水素 10h のための Def が指数関数グリッド上に作成されました

    Z: wavefunction の WKB Ansatz (n < Na=70))

plot_wavefunction(Z, 1:def.pos.Na, grid, def; reduced=true)
```

プロットは `CairomMakie` を使用して作成されます。注意: `plot_wavefunction` は `CamiXon` パッケージには含まれていません。 ![Image](../../assets/OUTSCH_H1_10h.png)
