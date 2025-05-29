```
Shells(name, shells)
```

閉じた電子[`Shells`](@ref)の仕様のための型で、フィールドは次のとおりです：

  * `.name`: シェル構成 (`::String`)
  * `.count`: シェルの数 (`::Int`)
  * `.n`: シェルの主量子数の配列 (`Vector{Int}`)
  * `.ℓ`: シェルの角運動量の配列 (`::Vector{Int}`)
  * `.shell`: Shellsの配列 (`::Vector{Shell}`)

型`Shells`は、関数`castShells`を使用して作成するのが最適です。
