```
obj = read_phantom_MRiLab(filename)
```

MRiLabファントムファイル`.mat`からPhantom構造体を返します。

# 引数

  * `filename`: (`::String`) ファントムファイル`.mat`の絶対パスまたは相対パス

# 返り値

  * `obj`: (`::Phantom`) Phantom構造体

# 例

```julia-repl
julia> obj_file = joinpath(dirname(pathof(KomaMRI)), "../examples/2.phantoms/brain.mat")

julia> obj = read_phantom_MRiLab(obj_file)

julia> plot_phantom_map(obj, :ρ)
```
