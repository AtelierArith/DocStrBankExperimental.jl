```
load_mesh(filename, type = Float64)
```

`filename`で指定されたファイルからメッシュをインポートします。サポートされているフォーマットにはstl、ply、obj、mshが含まれます。デフォルトでは、これは倍精度浮動小数点精度を使用する`Mesh`オブジェクトを生成します。ただし、`load_mesh(filename, Float32)`のように関連するデータ型を渡すことで、より低い精度を指定できます。

# 引数

  * `filename`: メッシュを含むファイルへのパス。
  * `type`: メッシュデータの浮動小数点精度タイプ（デフォルトは`Float64`）。

# 例

```julia
julia> mesh = load_mesh("path/to/mesh.obj");

julia> mesh = load_mesh("path/to/mesh.obj", Float32);
```
