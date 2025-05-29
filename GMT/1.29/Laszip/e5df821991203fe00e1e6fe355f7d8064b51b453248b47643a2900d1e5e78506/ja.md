```
argsout = lazread(FileName::AbstractString; out::String="xyz", type::DataType=Float64, class=0, startstop="1:end")
```

LIDAR laz（laszip圧縮）またはlas形式のファイルからデータを読み取ります。

  * `FileName`: 入力LIDARファイルの名前。

### キーワード引数

  * `out`: 出力するデータを選択します。デフォルトは「xyz」で、これらの3つのみが出力されます。例としては、「xyz」、「xy」、「yx」、「z」、「xyzi」、「xyzt」、「xyzit」、「xyzti」、「xyzic」、「xyzc」、「RGB」、「RGBI」があり、ここで 'i' は強度（UInt16）、'c' は分類（Int8）、't' はGPS時間（Float64）を表します。
  * `type`: floatコンポーネント（xyz）はFloat32で必要な場合があります。デフォルトはFloat64です。
  * `startstop="start:stop"`: 出力を開始から停止までのポイントに制限する文字列です。
  * `class`: 出力を分類 'class'（整数）に属するポイントに制限します。このオプションは、最初にクラス内のポイント数をカウントするための2回のパスを意味します。

### 戻り値

```
ARGSOUTはMx3のxyz配列に加えて、選択されたかどうかに応じて't'および|または'i'を含むタプルです
```

### 例

ファイル「lixo.laz」からx,y,z,tデータを読み取るには、次のようにします：

```julia
	xyz, t = lazread("lixo.laz", "xyzt")
```
