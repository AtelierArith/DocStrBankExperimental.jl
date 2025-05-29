```
defVar(ds::NCDataset,name,vtype,dimnames; kwargs...)
defVar(ds::NCDataset,name,data,dimnames; kwargs...)
```

データセット `ds` に名前 `name` の変数を定義します。 `vtype` は以下の表にあるJuliaの型（対応するNetCDF型）です。パラメータ `dimnames` は次元の名前のタプルです。スカラーの場合、このパラメータは空のタプル `()` です。変数は（型 `CFVariable` の）戻り値として返されます。

変数の型を指定する代わりに、NetCDF変数を埋めるために使用されるデータ `data` を直接提供することもできます。この場合、`dimnames` にある名前を使用して、必要に応じて適切なサイズの次元が作成されます。

`data` が `DateTime` オブジェクトのベクターまたは配列である場合、日付は倍精度浮動小数点数として保存され、単位は「1900-01-01 00:00:00 からの日数」となります（`attrib` キーワードで時間単位が指定されていない限り）。日付はCF変換のデフォルトカレンダーである混合ユリウス/グレゴリオ暦に変換されます。

## キーワード引数

  * `fillvalue`: 欠損データを示すためにNetCDFファイルに埋め込まれる値。 `_FillValue` 属性に保存されます。 `NCDatasets` はデータを読み込む際にデフォルトのNetCDFフィル値を暗黙的に使用しません。
  * `chunksizes`: チャンクサイズを設定する整数のベクター。チャンクの合計サイズは4 GiB未満でなければなりません。
  * `deflatelevel`: 圧縮レベル：0（デフォルト）は圧縮なし、9は最大圧縮を意味します。各チャンクは個別に圧縮されます。
  * `shuffle`: trueの場合、圧縮比を改善できるシャッフルフィルタが有効になります。
  * `checksum`: チェックサム方式は `:fletcher32` または `:nochecksum`（チェックサムが無効、これがデフォルト）です。
  * `attrib`: 属性名と属性値のペアの反復可能なコレクション、例えば `Dict`、`DataStructures.OrderedDict` または単にペアのベクター（以下の例を参照）
  * `typename`（文字列）：[vlen配列](https://web.archive.org/save/https://www.unidata.ucar.edu/software/netcdf/netcdf-4/newdocs/netcdf-c/nc_005fdef_005fvlen.html)に必要なNetCDF型の名前

`chunksizes`、`deflatelevel`、`shuffle`、および `checksum` はNetCDF 4ファイルにのみ設定できます。文字列と可変長配列の圧縮は、基盤となるNetCDFライブラリではサポートされていません。

## NetCDFデータ型

|   NetCDF型 |  Julia型 |
| ---------:| -------:|
|   NC_BYTE |    Int8 |
|  NC_UBYTE |   UInt8 |
|  NC_SHORT |   Int16 |
|    NC_INT |   Int32 |
|  NC_INT64 |   Int64 |
|  NC_FLOAT | Float32 |
| NC_DOUBLE | Float64 |
|   NC_CHAR |    Char |
| NC_STRING |  String |

## 次元の順序

データはメモリに格納されているのと同じ順序でNetCDFファイルに保存されます。Juliaは配列に[列優先順序](https://en.wikipedia.org/wiki/Row-_and_column-major_order)を使用しているため、データが[行優先順序](https://en.wikipedia.org/wiki/Row-_and_column-major_order)を使用する言語やプログラム（C/C++、Python/NumPy、またはツール `ncdump`/`ncgen` ([NetCDF CDL](https://web.archive.org/web/20220513091844/https://docs.unidata.ucar.edu/nug/current/_c_d_l.html))）で読み込まれると、次元の順序が逆に表示されます。NumPyも列優先順序を使用できますが、行優先順序がデフォルトです。次元の列優先解釈（Juliaのように）については、[CF規約は](https://web.archive.org/web/20220328110810/http://cfconventions.org/Data/cf-conventions/cf-conventions-1.7/cf-conventions.html#dimensions)「経度」（X）、「緯度」（Y）、「高さまたは深さ」（Z）、「日付または時間」（T）（該当する場合）の順序を推奨しています。その他の次元は、可能な限り、時空間次元の右側に配置されるべきです。

## 例：

この例では、`data` が保存されるときに `scale_factor` と `add_offset` が適用されます。

```julia-repl
julia> using DataStructures
julia> data = randn(3,5)
julia> NCDataset("test_file.nc","c") do ds
          defVar(ds,"temp",data,("lon","lat"), attrib = OrderedDict(
             "units" => "degree_Celsius",
             "add_offset" => -273.15,
             "scale_factor" => 0.1,
             "long_name" => "Temperature"
          ))
       end;
```

!!! note
    属性 `_FillValue`、`missing_value`、`add_offset`、`scale_factor`、`units` および `calendar` が使用される場合、それらは上記の例のように `attrib` パラメータを使用して `defVar` を呼び出す際に定義されるべきです。


```
