```
FV = surf2fv(X::Matrix{T}, Y::Matrix{T}, Z::Matrix{T}; type=:tri, bfculling=true,
             proj="", proj4="", wkt="", epsg=0, top=nothing, bottom=nothing) -> GMTfv
```

三次元のFacesVerticesオブジェクトを作成します。

この関数は、閉じた物体または3D表面のいずれかの3Dプロットに適しています。行列Zの値は、XおよびYによって定義されたx-y平面上のグリッドの高さを表します。

### 引数

  * `X,Y,Z`: 同じサイズと型の浮動小数点数の3つの行列。

### キーワード引数

  * `type`: 面のタイプ。$:tri$（デフォルト）または$:quad$のいずれかで、三角形または四角形の面を指定します。
  * `bfculling`: 見えない面のカリングを希望するかどうかを指定するブール値（デフォルトは$true$）。
  * `proj`または`proj4`: 座標参照系を設定するためのproj4文字列（オプション）。
  * `wkt`: WKT SRS（オプション）。
  * `epsg`: `proj`と同じですが、EPSGコードを使用します（オプション）。
  * `top`: 物体の上部を持つFaces 1行の行列（オプション）。この関数内では、$X$および$Y$行列の順序が何を表すかはもはやわからないため、これはすでに作成された面の行列である必要があります。
  * `bottom`: 物体の下部を持つFaces 1行の行列（オプション）。

### 例

```julia
X,Y = meshgrid(1:0.5:10,1.:20);
Z = sin.(X) .+ cos.(Y);
FV = surf2fv(X, Y, Z);
viz(FV)
```
