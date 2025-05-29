```
getraster(T::Union{Type{<:ModisProduct}, Type{MODIS{X}}}, [layer::Union{Tuple,AbstractVector,Integer, Symbol}]; kwargs...) => Union{String, AbstractVector, NamedTuple}
```

指定された[`ModisProduct`](@ref)の[`MODIS`](@ref)データをASCIIラスタとしてダウンロードします。

# 引数

  * `layer`: `Integer`または`Integer`または`Symbol`のタプル/範囲。`layer`引数がない場合、すべてのレイヤーがダウンロードされ、パスの`NamedTuple`が返されます。

特定の製品の利用可能なレイヤーは、[`RasterDataSources.layerkeys(T::Type{<:ModisProduct})`](@ref)を使用して調べることができます。

# キーワード

  * `lat`および`lon`: ラスタの近似中心の座標（小数度）。MODIS APIは、これらの座標にできるだけ近いピクセルグリッドシステムを一致させようとします。
  * `km_ab`および`km_lr`: ラスタの半幅および半高さ（上/下および左/右のキロメートル）。現在、`Integer`値のみがサポートされており、最大100までです。
  * `date`: リクエストの開始日と終了日の`String`、`Date`、`DateTime`、日付の`AbstractVector`または`Tuple`。`String`はYYYY-MM-DD形式である必要がありますが、`Dates.Date`によって理解可能な限り類似の形式でも構いません。MODISの利用可能な日付間隔は16日で、毎年1月1日にリセットされます。

# 例

フランスのブルターニュ西部で、2002年の冬から初夏までの250m NDVIをダウンロードします：

```julia
julia> getraster(MOD13Q1, :NDVI; lat = 48.25, lon = -4, km_ab = 50, km_lr = 50, date = (Date(2002,1,1), Date(2002,6,1)))

    10-element Vector{String}:
    "/your/path/MODIS/MOD13Q1/250m_16_days_NDVI/47.8313_-4.5899_2002-01-01.asc"
    ...
    "/your/path/MODIS/MOD13Q1/250m_16_days_NDVI/47.8313_-4.5899_2002-05-25.asc"
```

複数のファイルをダウンロードしようとし、各日付とレイヤーの組み合わせごとに1つずつ、ダウンロードされたまたは既存のファイルのファイルパスを返します。ファイル名の座標はラスタの左下隅に対応しています。
