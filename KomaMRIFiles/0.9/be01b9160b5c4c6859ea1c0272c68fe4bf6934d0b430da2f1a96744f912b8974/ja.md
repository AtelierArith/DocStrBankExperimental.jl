```
obj = read_phantom_jemris(filename)
```

JEMRISファントムファイル`.h5`からPhantom構造体を返します。

# 引数

  * `filename`: (`::String`) ファントムファイル`.h5`の絶対パスまたは相対パス

# 返り値

  * `obj`: (`::Phantom`) Phantom構造体

# 例

```julia-repl
julia> obj_file = joinpath(dirname(pathof(KomaMRI)), "../examples/2.phantoms/brain.h5")

julia> obj = read_phantom_jemris(obj_file)

julia> plot_phantom_map(obj, :ρ)
```
