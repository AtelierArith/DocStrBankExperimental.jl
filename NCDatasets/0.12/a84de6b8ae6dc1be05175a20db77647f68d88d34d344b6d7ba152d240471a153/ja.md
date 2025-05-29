```
NCDataset(filename::AbstractString, mode = "r";
          format::Symbol = :netcdf4,
          share::Bool = false,
          diskless::Bool = false,
          persist::Bool = false,
          memory::Union{Vector{UInt8},Nothing} = nothing,
          attrib = [])
```

`mode`に応じて、`filename`でNetCDFファイルを読み込み、作成、または上書きします。

  * `"r"` (デフォルト) : 既存のnetCDFファイルまたはOPeNDAP URLを読み取り専用モードで開きます。
  * `"c"` : `filename`に新しいNetCDFファイルを作成します（同じ名前の既存のファイルは上書きされます）。
  * `"a"` : `filename`を追加モードで開きます（すなわち、netCDFファイル内の既存のデータは上書きされず、変数を追加できます）。

`share`がtrueの場合、`NC_SHARE`フラグが設定され、複数のプロセスがファイルを読み取り、1つのライタープロセスを持つことができます。同様に、`diskless`または`persist`をtrueに設定すると、`NC_DISKLESS`または`NC_PERSIST`フラグが有効になります。詳細は[NetCDF C-API](https://www.unidata.ucar.edu/software/netcdf/docs/)で確認できます。

これはデータセットを閉じないことに注意してください。結果に対して`close`を使用するか、以下の`do`ブロックを参照してください。

オプションのパラメータ`attrib`は、属性名と属性値のペアのイテラブルであり、例えば`Dict`、`DataStructures.OrderedDict`、または単にペアのベクター（以下の例を参照）です。

# サポートされている`format`の値:

  * `:netcdf4` (デフォルト): HDF5ベースのNetCDFフォーマット。
  * `:netcdf4_classic`: netCDF 3互換API機能のみが使用されます。
  * `:netcdf3_classic`: 2GB未満のファイルのみをサポートするクラシックnetCDFフォーマット。
  * `:netcdf3_64bit_offset`: 2GBを超えるファイルをサポートする改善されたnetCDFフォーマット。
  * `:netcdf5_64bit_data`: 64ビット整数データ型をサポートする改善されたnetCDFフォーマット。

ファイルは`do`ブロックを使用して開き、自動的に閉じることもできます。

```julia
NCDataset("file.nc") do ds
    data = ds["temperature"][:,:]
end
```

属性の例は次のとおりです。

```julia
using DataStructures
NCDataset("file.nc", "c", attrib = OrderedDict("title" => "my first netCDF file")) do ds
   defVar(ds,"temp",[10.,20.,30.],("time",))
end;
```

NetCDFデータセットは、バイトのベクターとして`memory`であることもできます。非空の文字列`filename`は依然として必要です。例えば：

```julia
using NCDataset, HTTP
resp = HTTP.get("https://www.unidata.ucar.edu/software/netcdf/examples/ECMWF_ERA-40_subset.nc")
ds = NCDataset("some_string","r",memory = resp.body)
total_precipitation = ds["tp"][:,:,:]
close(ds)
```

`Dataset`は`NCDataset`のエイリアスです。
