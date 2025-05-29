```
castShells(strShells::String; msg=false)
```

閉じた電子[`Shells`](@ref)の構成を作成します。フィールドは次のとおりです。

  * `.name`: シェル構成 (`::String`)
  * `.count`: シェルの数 (`::Int`)
  * `.n`: シェルの主量子数の配列 (`Vector{Int}`)
  * `.ℓ`: シェルの角運動量の配列 (`::Vector{Int}`)
  * `.shell`: Shellsの配列 (`::Vector{Shell}`)

#### 例:

```
julia> castShells("1s2s",msg=true);
Shell: 1s²
    shell電子の数: N = 2
    主量子数: n = 1
    電子の軌道角運動量: ℓ = 0
Shell: 2s²
    shell電子の数: N = 2
    主量子数: n = 2
    電子の軌道角運動量: ℓ = 0
```
