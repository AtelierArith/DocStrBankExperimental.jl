```
TiledView(data::F, tile_size::NTuple{N,Int}, 
          tile_overlap::NTuple{N,Int} = tile_size .* 0, 
          tile_center::NTuple{M,Int} = (mod.(tile_size,2) .+ 1)
          ; pad_value::T, keep_center=true)
```

N次元データをtile*size、tile*overlap、およびオプションでtile_centerによって指定されたタイルでタイル状に配置することによって、2N次元のビューを作成します。

## 引数

  * `data`: TiledViewに分解する入力データ。`TiledView`のためにコピーは作成されず、生データは`.parent`を介してアクセスできます。
  * `tile_size`: 各タイルのサイズを説明するタプル。このサイズは`size(myview)`の結果の最初のN次元を形成します。次のN次元はN次元タイルの番号を指します。
  * `tile_overlap`: ボクセル単位での連続するタイル間のオーバーラップを指定するタプル。これは暗黙的にタイル間のピッチを`(tile_size .- tile_overlap)`として定義します。

## キーワード引数

  * `pad_value`: ソース配列の外部の位置に`get_index`が適用されたときに返される値を指定します。
  * `keep_center`: このブール値は、親`data`の中心が中央タイルの中心と整列するかどうかを指定します。`false`の場合、最初のタイルはオフセットゼロから始まります。
  * `tile_center`: `keep_center`がtrueの場合のみ使用されます。中央タイルの中心位置を定義します。デフォルトは`tile_size .÷ 2 .+1`です。

# 例

```jldoctest TiledView
julia> a = TiledView(reshape(1:49,(7,7)), (4, 4),(1, 1));

julia> a.parent
7×7 reshape(::UnitRange{Int64}, 7, 7) with eltype Int64:
 1   8  15  22  29  36  43
 2   9  16  23  30  37  44
 3  10  17  24  31  38  45
 4  11  18  25  32  39  46
 5  12  19  26  33  40  47
 6  13  20  27  34  41  48
 7  14  21  28  35  42  49

julia> size(a)
(4, 4, 3, 3)
```
