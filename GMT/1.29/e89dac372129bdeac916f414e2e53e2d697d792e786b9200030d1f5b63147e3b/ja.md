```
G = mat2grid(mat; reg=nothing, x=[], y=[], v=[], hdr=[], proj4::String="", wkt::String="",
             title::String="", rem::String="", cmd::String="", names::Vector{String}=String[],
             scale::Float32=1f0, offset::Float32=0f0, eqc=false)
```

2/3Dの`mat`配列とHDR 1x9 [xmin, xmax, ymin, ymax, zmin, zmax, reg, xinc, yinc] ヘッダ記述子を取り、GMTgridタイプのグリッドを返します。HDRの代わりに、XおよびY座標を持つベクトル`x`と`y`のペアを提供します。オプションで、`mat`が3D配列であり、$cube$を作成したい場合は、垂直座標を持つ`v`ベクトルを追加できます。HDR引数は省略可能で、`mat`のみから計算されますが、その場合x=1:ncol, y=1:nrowになります。HDRが使用されない場合、REG == nothing [デフォルト]はグリッドライン登録グリッドを作成し、REG = 1またはREG="pixel"はピクセル登録グリッドを意味します。

  * `eqc`: trueの場合、座標のない等距離円筒投影を表す行列を取得したことを意味します。出力グリッドは[-180 180]および[-90 90]の間のグローバル座標を持ちます。xincおよびyincは、`mat`のサイズと、次元が偶数（ピクセル）または奇数（グリッド）に基づく登録タイプの推測から計算されます。`reg`オプションで登録の推測を上書きします。地球以外の天体の場合、ユーザーは`proj4`オプションを指定する必要があります。

3D配列の場合、`names`オプションは各層の説明を提供するために使用されます（GDAL関数を使用する際にファイルに保存されます）。

`scale`および`offset`オプションは、`mat`が整数型であり、スケール/オフセットでグリッドを保存したい場合に使用されます。  

---

この関数の他のメソッドは次のようにします：

```
G = mat2grid(val=0.0f; hdr=hdr_vec, reg=0, proj4::String="", wkt::String="", title::String="", rem::String="")
```

サイズ、座標、およびインクリメントがHDR変数の内容によって決定されるFloat GMTgridを作成します。この配列は、上記と同じ意味を持つか、または、[xmin xmax ymin ymax xinc yinc]のみを含む必要があります。VALは行列を埋める値です（デフォルトVAL = Float32(0)）。Float64配列を取得するには、たとえばVAL = 1.0を使用します。他のFloat64以外の値はFloat32に変換されます。

```
例: mat2grid(1, hdr=[0. 5 0 5 1 1])
```

```
G = mat2grid(f::Function, x, y; reg=nothing, proj4::String="", wkt::String="", epsg::Int=0, title::String="", rem::String="")
```

ここでFは関数で、X,Yはその定義域を定義するベクトル座標です。XおよびYベクトルのサイズによって決定されるFloat32 GMTgridを作成します。

```
例: f(x,y) = x^2 + y^2;  G = mat2grid(f, x = -2:0.05:2, y = -2:0.05:2)
```

```
G = mat2grid(f::String)
```

ここでfはプリセット関数名です。現在利用可能なもの：

  * "ackley", "eggbox", "sombrero", "parabola" および "rosenbrock"

X,Yは関数の定義域を定義するベクトル座標ですが、各関数に対してデフォルト値が提供されています。Float32 GMTgridを作成します。

```
例: G = mat2grid("sombrero")
```
