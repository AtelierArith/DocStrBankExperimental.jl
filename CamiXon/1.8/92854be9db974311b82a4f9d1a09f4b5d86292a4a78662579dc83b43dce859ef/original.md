OUTSCH!(Z::Vector{Complex{T}}, E::T, grid::CamiDiff.Grid{T}, def::Def{T}, adams::Adams{T}) where T<:Real

Ansatz solution for the *outward* integration of the radial wave equation for the first $k$ points  on the [`CamiDiff.Grid`](@extref), where $k$ is the Adams-Moulton order. For angular momentum `0 ≤ ℓ ≤ 5` the  Walter Johnson Ansatz is used; for $ℓ > 5$ the Ansatz is based on the WKB solution for energy `E`  at distances *far below* the inner classical turning point - ictp)

#### Example:

```
Ecal, grid, def, adams = demo_hydrogen(n=1, ℓ=0)
Z = OUTSCH(Ecal, grid, def, adams.σ)
println("\nZ: standard Ansatz for wavefunction (n < Na=$(def.pos.Na)))")
    Orbital: 1s
        principal quantum number: n = 1
        radial quantum number: n′ = 0 (number of nodes in radial wavefunction)
        orbital angular momentum of valence electron: ℓ = 0
    CamiDiff.Grid created: exponential, Float64, Rmax = 63.0 a.u., N = 100, h = 0.1, r0 = 0.00286033
    Def created for hydrogen 1s on exponential grid

    Z: standard Ansatz for wavefunction (n < Na=8))

Ecal, grid, def, adams = demo_hydrogen(n=10, ℓ=5)
Z = OUTSCH(Ecal, grid, def, adams.σ);
println("\nZ: WKB Ansatz for wavefunction (n < Na=$(def.pos.Na)))")
    Orbital: 10h
        principal quantum number: n = 10
        radial quantum number: n′ = 4 (number of nodes in radial wavefunction)
        orbital angular momentum of valence electron: ℓ = 5
    CamiDiff.Grid created: exponential, Float64, Rmax = 360.0 a.u., N = 550, h = 0.0181818, r0 = 0.0163447
    Def created for hydrogen 10h on exponential grid

    Z: WKB Ansatz for wavefunction (n < Na=70))

plot_wavefunction(Z, 1:def.pos.Na, grid, def; reduced=true)
```

The plot is made using `CairomMakie`. NB.: `plot_wavefunction` is not included in the `CamiXon` package. ![Image](../../assets/OUTSCH_H1_10h.png)
