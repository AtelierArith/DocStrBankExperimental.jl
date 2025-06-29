```
I = mosaic(lon, lat; pt_radius=6378137.0, provider="", zoom::Int=0, cache::String="",
           mapwidth=15, dpi=96, verbose::Int=0, kw...)
```

指定された経度、緯度座標からウェブマップタイルプロバイダーから画像タイルを取得します。

### 引数

  * `lon` & `lat`:

      * `lon, lat`: 興味のある地域の中心の座標を持つ2つのスカラー。画像エリアを完全に定義するには、以下の`neighbors`または`mosaic`オプションを参照してください。
      * `lon, lat`は地域の[lon*min, lon*max], [lat*min, lat*max]を持つ2要素のベクトルまたは行列です。
      * 2つの引数の代わりに、$geocoder$関数で取得したGMTdatasetを含む1つの引数を渡します。例: $mosaic(D, ...)$または、$geocoder$での検索が十分に一般的であった場合（そのドキュメントを参照）、$mosaic(D, bbox=true)$を使用してクエリによって返されたBoundingBoxを使用します。`bbox`は`bb`、`BB`または`BoundingBox`のエイリアスをサポートします。
      * もう1つの代替手段は、有効な投影を持つGMTgridまたはGMTimageを渡すことで、地理座標である必要はありません。他の参照系の座標は地理座標に変換されます。
      * 最後に、キーワード`region`が使用される場合、上記のすべてのオプションをスキップできます。このオプションは、例えば、$coast$モジュールと同じであることに注意してください。つまり、$earthregions$引数と一緒に使用できます。*例* $region="IT"$は有効なオプションで、イタリアの画像を構築するために必要なタイルを取得します。
  * `pt_radius`: 惑星の半径。デフォルトは地球のWGS84赤道半径（6378137 m）です。
  * `provider`: タイルプロバイダー名。現在利用可能なオプションは（詳細については`getprovider`関数のドキュメントを参照してください、*すなわち* $? getprovider$）:

      * "Bing"（デフォルト）、"Google"、"OSM"、"Esri"またはカスタムプロバイダー。
      * $$
        TileProviders.jl
        $$

        パッケージの`Provider`型。プロバイダーを選択する方法についての詳細は、そのパッケージのドキュメントを参照する必要があります。
  * `zoom`: ズームレベル（自動の場合は0）。0から約19の間の数値。最大値はプロバイダーとエリアに依存します。`zoom=0`の場合、ズームレベルは`mapwidth`と`dpi`オプションに基づいて自動的に計算されます。
  * `cache`: ダウンロードしたタイルを保存するキャッシュディレクトリのフルネーム。空の場合、システムのTMPディレクトリにキャッシュディレクトリが作成されます。`cache="gmt"`の場合、キャッシュディレクトリは$~/.gmt/cache_tileserver$に作成されます。注意: これは通常、この関数を初めて実行する際にのみ必要で、`cache!=""`の場合、キャッシュディレクトリの場所が$~./gmt/tiles_cache_dir.txt$ファイルに保存され、以降の呼び出しで使用されます。
  * `mapwidth`: cm単位の地図の幅。ズームレベルを自動的に計算するために`dpi`オプションと一緒に使用されます。
  * `dpi`: インチあたりのドット数。ズームレベルを自動的に計算するために`mapwidth`オプションと一緒に使用されます。
  * `verbose`: 冗長性レベル。0から2の間の数値。画像ファイルをダウンロード中に情報を出力します。ローカルキャッシュからファイルを取得する際は静かですが、`verbose=2`の場合、キャッシュ内で見つかったファイルに関する情報を出力します。

### kwargs (kw...)

  * `neighbors`または`mosaic`: `lon`と`lat`がスカラーの場合、このオプションはクエリポイントを含むタイルの隣接数を指定します。通常、これは奇数であるべきですが、行列の形を取ることもでき、その場合はタイルの数は行と列の数によって決まります。
  * `merc`または`mercator`: メルカトル座標でタイル画像を返します。デフォルトは地理座標に戻すことです。
  * `loose`または`loose_bounds`: デフォルトでは、`lon`と`lat`引数で要求された制限を持つ画像を返します。このオプションを使用すると、要求された地域と交差するタイルの制限によって決定される制限を持つ画像が返されます。これはポイントクエリには機能しないことに注意してください。
  * `quadonly`: クワッドツリー文字列のみを返します。タイルの数が1より大きい場合は、文字列または文字列の行列です。クワッドツリー文字列の他に、このオプションは`decimal_adress, lon, lat, x, y`も返します。これらは、XYZタイルの座標、経度、緯度、メルカトルXおよびY座標（最初のタイルのメートル単位）です。
  * `tilesmesh`または`meshtiles`または`mesh`: タイルのメッシュを持つ`GMTdataset`を返します。

### 戻り値

  * `I`: GMTimage要素または上記で説明した`quadonly`オプションの出力。

# 例

```jldoctest
julia> I = mosaic(0.1,0.1,zoom=1)
viz(I, coast=true)
```

```jldoctest
# タイルのメッシュを持つGMTdatasetを返し、可視化します。
D = mosaic(region=(-10, -8, 37, 39), zoom=9, mesh=true);
viz(D, coast=true)
```
