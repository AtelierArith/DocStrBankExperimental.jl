```
castOrbit(;n=1, ℓ=0, mℓ=0, msg=true)
```

Create `Orbit` with fields:

  * `.name`: name
  * `.n`:  principal quantum number
  * `.n′`:  radial quantum number (number of nodes in radial wavefunction)
  * `.ℓ`:  orbital angular momentum valence electron
  * `.mℓ`:  orbital angular momentum projection valence electron

#### Example:

```
julia> castOrbit(n=1, ℓ=0; msg=true)
Orbital: 1s
    principal quantum number: n = 1
    radial quantum number: n′ = 0 (number of nodes in radial wavefunction)
    orbital angular momentum of valence electron: ℓ = 0
    orbital angular momentum projection of valence electron: mℓ = 0
Orbit("1s", 1, 0, 0, 0)
```

```
castOrbit(strOrbit::String; mℓ=0, msg=false)
```

#### Example:

```
julia> castOrbit("2p"; mℓ=-1, msg=true)
Orbital: 2p
    principal quantum number: n = 2
    radial quantum number: n′ = 0 (number of nodes in radial wavefunction)
    orbital angular momentum of valence electron: ℓ = 1
    orbital angular momentum projection of valence electron: mℓ = -1
Orbit("2p", 2, 0, 1, -1)
```
