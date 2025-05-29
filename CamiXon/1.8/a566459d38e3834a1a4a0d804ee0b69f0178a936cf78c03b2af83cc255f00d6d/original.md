```
castShell(;n=1, ℓ=0, msg=false)
```

Create closed electron [`Shell`](@ref) with fields:

  * `.name`: shell configuration (`::String`)
  * `.spinorbit`: Array of Spinorbitals (`::Vector{Spinorbit}`)

#### Example:

```
julia> castShell(n=1, ℓ=0, msg=true)
Shell: 3s²
    number of shell electrons: N = 2
    principal quantum number: n = 3
    orbital angular momentum of electrons: ℓ = 0
Shell("3s²", Spinorbit[Spinorbit("3s↓", Orbit("3s", 3, 2, 0, 0), -1//2), Spinorbit("3s↑", Orbit("3s", 3, 2, 0, 0), 1//2)])
```

```
castShell(strShell::String; msg=false)
```

#### Example:

```
julia> castShell("3s", msg=false)
Shell("3s²", Spinorbit[Spinorbit("3s↓", Orbit("3s", 3, 2, 0, 0), -1//2), Spinorbit("3s↑", Orbit("3s", 3, 2, 0, 0), 1//2)])
```
