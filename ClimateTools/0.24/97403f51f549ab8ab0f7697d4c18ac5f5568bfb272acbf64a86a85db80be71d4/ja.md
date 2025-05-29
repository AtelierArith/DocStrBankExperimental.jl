```
load(file::String, vari::String; poly = Array{Float64}([]), start_date::Tuple, end_date::Tuple, data_units::String = "")
```

**file**の変数**vari**のデータをポリゴン**poly**内で持つClimGrid型を返します。メタデータはnetCDF属性からClimGrid型に組み込まれています。

ClimGrid型の内部では、データは時間、経度/x、および緯度/yの次元を持つAxisArrayデータ型に格納されています。

提供されたポリゴンは-180、+180経度形式である必要があります。ポリゴンが国際日付変更線を越える場合、ポリゴンは複数の部分（すなわちマルチポリゴン）に分割する必要があります。

data_unitsのオプションは降水量の場合は「mm」で、これはnetCDFファイルで見られる通常の「kg m-2 s-1」単位を変換します。温度の場合は「Celsius」で、これは通常の「Kelvin」単位を変換します。

時間的サブセットは、長さ1（年）、長さ3（年、月、日）、または長さ6（時間、分、秒）のタプルを提供することで行うことができます。

**注意:** loadは[CF conventions](http://cfconventions.org/)を使用します。loadでnetCDFファイルを読み取れない場合、ユーザーは[NetCDF.jl package](https://github.com/JuliaGeo/NetCDF.jl)または[NCDatasets.jl](https://github.com/Alexander-Barth/NCDatasets.jl)で利用可能な低レベル関数を使用して読み取るか、標準化されたnetCDFファイルを再作成する必要があります。
