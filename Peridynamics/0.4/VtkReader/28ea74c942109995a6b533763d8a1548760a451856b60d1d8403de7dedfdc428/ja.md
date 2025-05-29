```
read_vtk(file::AbstractString)
```

時間ステップのシミュレーション結果を含むvtuまたはpvtuファイルを読み込みます。

# 引数

  * `file::String`: vtuまたはpvtu形式のVTKファイルへのパス。

# 戻り値

  * `Dict{String, VecOrMat{Float64}}`: 辞書としてのシミュレーション結果。

# 例

```julia-repl
julia> read_vtk("results/fragmenting_cylinder/vtk/timestep_000520.pvtu")
Dict{Symbol, VecOrMat{Float64}} with 4 entries:
  :position     => [0.0263309 0.027315 … 0.0293543 0.030339; 0.000292969 0.000294475…
  :displacement => [0.00583334 0.00581883 … 0.00585909 0.00584271; -0.000162852 -0.0…
  :damage       => [0.616071, 0.569343, 0.528571, 0.463415, 0.438776, 0.553571, 0.56…
  :time         => [9.69363e-5]
```
