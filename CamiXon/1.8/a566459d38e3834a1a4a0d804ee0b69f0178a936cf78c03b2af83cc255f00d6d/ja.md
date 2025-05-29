```
castShell(;n=1, ℓ=0, msg=false)
```

閉じた電子 [`Shell`](@ref) を作成し、フィールドを持ちます：

  * `.name`: シェルの構成 (`::String`)
  * `.spinorbit`: スピン軌道の配列 (`::Vector{Spinorbit}`)

#### 例：

```
julia> castShell(n=1, ℓ=0, msg=true)
Shell: 3s²
    シェル電子の数: N = 2
    主量子数: n = 3
    電子の軌道角運動量: ℓ = 0
Shell("3s²", Spinorbit[Spinorbit("3s↓", Orbit("3s", 3, 2, 0, 0), -1//2), Spinorbit("3s↑", Orbit("3s", 3, 2, 0, 0), 1//2)])
```

```
castShell(strShell::String; msg=false)
```

#### 例：

```
julia> castShell("3s", msg=false)
Shell("3s²", Spinorbit[Spinorbit("3s↓", Orbit("3s", 3, 2, 0, 0), -1//2), Spinorbit("3s↑", Orbit("3s", 3, 2, 0, 0), 1//2)])
```
