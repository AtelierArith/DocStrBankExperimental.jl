```
ncvar_def(ds, name, val, dims::Vector{<:AbstractString}, attrib = Dict();
    compress = 1, kw...)
ncvar_def(ds, name, val, dims::NcDim, attrib = Dict();
    compress = 1, kw...)
```

# 引数

  * `val`: `data` または vtype であることができます
  * `compress`: 圧縮レベル: 0（デフォルト）は圧縮なしを意味し、9は最大圧縮を意味します。各チャンクは個別に圧縮されます。
  * `type`: どのタイプを保存しますか？ Juliaの変数タイプ（文字列ではない）、例: `Float32`。
  * `options`: 辞書オブジェクト、 

      * `fillvalue`: 欠損データを示すためにNetCDFファイルに埋め込まれる値。これは_FillValue属性に保存されます。
      * `chunksizes`: チャンクサイズを設定する整数のベクター。チャンクの合計サイズは4 GiB未満でなければなりません。
      * `shuffle`: trueの場合、シャッフルフィルターが有効になり、圧縮比が改善される可能性があります。
      * `checksum`: チェックサムメソッドは:fletcher32または:nochecksum（チェックサムが無効になり、これがデフォルト）です。
      * `attrib`: 属性名と属性値のペアの反復可能なコレクション、例えばDict、DataStructures.OrderedDict、または単にペアのベクター（以下の例を参照）

# 例

```julia
f = "f1.nc"
isfile(f) && rm(f)
ds = nc_open(f, "c")
compress = 1

ncdim_def(ds, "lon", lon, Dict("longname" => "Longitude", "units" => "degrees east"))
ncdim_def(ds, "lat", lat, Dict("longname" => "Latitude", "units" => "degrees north"))
ncdim_def(ds, "time", 1:ntime)

ncvar_def(ds, "HI", dat, ["lon", "lat", "time"], Dict("longname" => "hello"); compress = compress)
close(ds)

# 変数を追加
ds = nc_open(f, "a")
ncvar_def(ds, "HI2", dat, ["lon", "lat", "time"]; compress = compress)
print(ds)
close(ds)

nc_info(f)
```

@seealso [`ncdim_def`](@ref)
