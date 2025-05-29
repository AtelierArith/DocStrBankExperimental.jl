```
Mesh(type = Float64)
```

空の三角形密なメッシュを生成し、原始的または3Dシーンを表します。デフォルトでは、`Mesh`オブジェクトは倍精度浮動小数点数（`Float64`）の座標のみを受け入れますが、`Mesh(Float32)`のように対応するデータ型を指定することで、より低い精度を生成できます。

# 引数

  * `type`: メッシュデータの浮動小数点精度タイプ（デフォルトは`Float64`）。

# 戻り値

頂点や法線を持たない`Mesh`オブジェクト。

# 例

```jldoctest
julia> m = Mesh();

julia> nvertices(m);

julia> ntriangles(m);

julia> Mesh(Float32);
```
