```
polyhedron2particle(stl_file::String, output_file, h; method::String="voxel", 
    verbose::Bool=false)
```

## 説明:

ポリヘドロン（`.stl`）を粒子のセットに変換します。この関数は、各ボクセルの populated 粒子を `.xyz` ファイルに書き込みます。ボクセルサイズは `h` によって定義され、MPM 背景グリッドサイズと等しいことが推奨されます。`method` は文字列で "voxel" または "ray" になります。`verbose` は各ステップの時間消費を表示するためのフラグです。

## 例:

```julia
stl_file = "/path/to/your/model.stl"
output_file = "/path/to/your/model.xyz"
h = 0.1
polyhedron2particle(stl_file, output_file, h, verbose=true)
```
