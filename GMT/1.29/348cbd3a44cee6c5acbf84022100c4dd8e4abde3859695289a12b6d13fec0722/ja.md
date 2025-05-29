```
FV = revolve(curve::Matrix{Real}; extent = 360, ang1=0, ang2=360, dir=:positive, n=[0.0,0.0,1.0], n_steps=0, closed=true, type=:quad) -> GMTfv
```

曲線を回転させて表面を構築します。

この関数は、ベクトル `n` の周りに、方向 `direction`（`:positive`、`:negative`、`:both`）で角度 `extent` だけ曲線 `curve` を回転させて、Faces-Vertices タイプとして定義された出力メッシュを構築します。

### クレジット

この関数は、`Comodo.jl` パッケージの `revolvecurve` 関数の修正版です。

### 引数

  * `curve`: 回転させる曲線を定義する Mx3 の点の行列。各行は3D空間の点です。

### キーワード引数

  * `extent`: 回転させた曲線の範囲（度）。デフォルトは360度ですが、`ang1` と `ang2` 引数を使用することでより細かい制御が可能です。
  * `ang1`: 開始角度（度）。開始角度と終了角度が完全な回転を定義しない場合に使用します。
  * `ang2`: 終了角度（度）。
  * `dir`: 回転させた曲線の方向（`:positive`、`:negative`、`:both`）。
  * `n`: 回転させた曲線の法線ベクトル。
  * `n_steps`: 回転させた曲線を構築するために使用されるステップ数。`0`（デフォルト）の場合、ステップ数は曲線の点間隔から計算されます。
  * `closed`: `true`（デフォルト）の場合、開始スライスと終了スライスで回転させた曲線を閉じます。
  * `type`: 回転させた曲線を構築するために使用される面のタイプ（`:quad`（デフォルト）、`:tri`）。

### 戻り値

  * `FV`: Faces-Vertices データセット。

### 例

```julia
ns=15; x=linspace(0,2*pi,ns).+1; y=zeros(size(x)); z=-cos.(x); curve=[x[:] y[:] z[:]];
FV = revolve(curve)
viz(FV, pen=0)
```
