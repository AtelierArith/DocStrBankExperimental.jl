```julia
nc_write(
    f::AbstractString,
    varname::AbstractString,
    val,
    dims::Vector{NetCDFTools.NcDim};
    ...
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}
nc_write(
    f::AbstractString,
    varname::AbstractString,
    val,
    dims::Vector{NetCDFTools.NcDim},
    attrib::Dict;
    overwrite,
    mode,
    kw...
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}

```

# 引数

  * `mode`: "r", "c", "w" のいずれか、詳細は [NCDatasets.nc_open()] を参照

      * "a": 追加
      * "c": 作成
  * `units`: 変数の単位
  * `longname`: 変数の長い名前
  * attrib: 属性名と属性値のペアのイテラブル、例えば Dict、DataStructures.OrderedDict または単にペアのベクター（下の例を参照）
  * `type`: どのタイプを保存するか？ Julia の変数タイプ。
  * `kwargs`: `ncvar_def` に渡されるパラメータ、さらに [`NCDatasets.defVar`] に渡される。例：

      * fillvalue: 欠損データを示すために NetCDF ファイルに埋め込まれる値。_FillValue 属性に保存される。
      * chunksizes: チャンクサイズを設定する整数のベクター。チャンクの合計サイズは 4 GiB 未満でなければならない。例えば `(10, 10, 1)`
      * shuffle: true の場合、シャッフルフィルターが有効になり、圧縮率が向上する可能性がある。
      * checksum: チェックサム方式は :fletcher32 または :nochecksum （チェックサムが無効、デフォルト）にすることができる。

# 例

```julia
dims = [
    NcDim("lon", lon, Dict("longname" => "Longitude", "units" => "degrees east"))
    NcDim("lat", lat, Dict("longname" => "Latitude", "units" => "degrees north"))
    NcDim_time(dates)
]

b = bbox(70, 15, 140, 55)
cellsize=1
dates = Date(2010):Day(1):Date(2010, 1, 4) |> collect
dims = NcDims(b, cellsize, dates) # 一つのオプション

nc_write(f, varname, val, dims; units, longname)
```

```julia
nc_write(f, varname, val, dims; ...)
nc_write(
    f,
    varname,
    val,
    dims,
    attrib;
    overwrite,
    mode,
    kw...
)
```

[`packages/NetCDFTools/QX4TD/src/nc_write.jl:55`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/nc_write.jl) で定義されています。

@seealso `ncvar_def`
