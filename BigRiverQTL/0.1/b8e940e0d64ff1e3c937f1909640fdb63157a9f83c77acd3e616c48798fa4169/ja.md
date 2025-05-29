```
 shrinkg(f,nb::Int64,geno)
```

フルランクの正定値親族行列を収縮強度推定（ブートストラップ）によって推定します。これは[`kinship_man`](@ref)、[`kinship_4way`](@ref)でのみ使用できます。この関数はCPUの並列化によってより速く実行されます。速度向上のために、実行前に`addprocs()`関数を使用してワーカー/プロセスを追加してください。

# 引数

  * `f`: 親族を計算する関数。これは[`kinship_man`](@ref)、[`kinship_4way`](@ref)でのみ使用できます。
  * `nb` : ブートストラップの数を示す整数。大きな数である必要はありません。
  * `geno` : ジェノタイプの行列。次元については[`kinship_man`](@ref)、[`kinship_4way`](@ref)を参照してください。

# 例

```julia
julia> using flxQTL
julia> addprocs(8)
julia> K = shinkage(kinshipMan,20,myGeno)
```

# 出力

_ フルランクの対称正定値行列を返します。 ```
