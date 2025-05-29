```
castSpinorbit(;n=1, ℓ=0, mℓ=0, up=true, msg=false)
```

Create `Spinorbit` with fields:

  * `.name`: spinorbital name (string)
  * `.n`:  principal quantum number
  * `.n′`:  radial quantum number (number of nodes in radial wavefunction)
  * `.ℓ`:  orbital angular momentum valence electron
  * `.mℓ`:  orbital angular momentum projection valence electron
  * `.ms`: spin magnetic quantum number (Rational{Int})

#### Example:

```
julia> castSpinorbit(n=1, ℓ=0, msg=true)
Spinorbital: 1s↑
    principal quantum number: n = 1
    radial quantum number: n′ = 0 (number of nodes in radial wavefunction)
    orbital angular momentum of valence electron: ℓ = 0
    orbital angular momentum projection of valence electron: mℓ = 0
    spin magnetic quantum number: ms = 1/2
Spinorbit("1s↑", 1, 0, 0, 0, 1//2)
```

```
castSpinorbit(config::String; msg=false)
```

#### Example:

```
julia> castSpinorbit1("2p"; msg=true)
Spinorbital: 2p↓
    principal quantum number: n = 2
    radial quantum number: n′ = 0 (number of nodes in radial wavefunction)
    orbital angular momentum of valence electron: ℓ = 1
    orbital angular momentum projection of valence electron: mℓ = 1
    spin magnetic quantum number: ms = -1/2
Spinorbit("2p↓", 2, 0, 1, 1, -1//2)

julia> castSpinorbit1("2p↑-1"; msg=true)
Spinorbital: 2p↑
    principal quantum number: n = 2
    radial quantum number: n′ = 0 (number of nodes in radial wavefunction)
    orbital angular momentum of valence electron: ℓ = 1
    orbital angular momentum projection of valence electron: mℓ = -1
    spin magnetic quantum number: ms = 1/2
Spinorbit("2p↑", 2, 0, 1, -1, 1//2)
```
