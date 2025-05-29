```
mfds = NCDataset(fnames, mode = "r"; aggdim = nothing, deferopen = true,
              isnewdim = false,
              constvars = [])
```

読み取り専用の `"r"` または追加モードの `"a"` でマルチファイルデータセットを開きます。 `fnames` はファイル名のベクターです。

変数は、最初の無制限次元または指定された次元 `aggdim` にわたって集約されます。次元 `aggdim` を持たない変数は集約されません。次元 `aggdim` を含むすべての変数が集約されます。次元 `aggdim` を含まない変数は定数であると見なされます。

変数を新しい次元（NetCDFファイルに存在しない）にわたって集約する必要がある場合は、`isnewdim` を `true` に設定する必要があります。すべてのNetCDFファイルは同じ変数、属性、およびグループを持っている必要があります。デフォルトでは、すべての変数は追加の次元を持ちますが、`constvars` パラメータを使用して定数としてマークされている場合は除きます。

追加モードは、`deferopen` が `false` の場合にのみ実装されています。`deferopen` が `false` の場合、すべてのファイルが同時に開かれます。ただし、オペレーティングシステムはオープンファイルの数を制限する場合があります。Linuxでは、制限は [コマンド `ulimit`](https://stackoverflow.com/questions/34588/how-do-i-change-the-number-of-open-files-limit-in-linux) で制御できます。

すべてのメタデータ（属性と次元の長さ）は、すべてのNetCDFファイルで同じであると見なされます。そうでなければ、マルチファイルデータセットの属性を読み取ることはあいまいになります。このルールの例外は、データが集約される次元の長さです。この集約次元は、ファイルごとに異なる場合があります。

実験的フラグ `_aggdimconstant` を `true` に設定すると、集約次元の長さが一定であることを意味します。これにより、マルチファイルデータセットの作成が高速化され、最初のファイルのメタデータのみをロードする必要があります。

例：

ファイルパターンから `fnames` を作成するには、[Glob.jl](https://github.com/vtjnash/Glob.jl) を使用できます。例えば：

```julia
using NCDatasets, Glob
ds = NCDataset(glob("ERA5_monthly3D_reanalysis_*.nc"))
```

新しい次元にわたる集約：

```julia
using NCDatasets
for i = 1:3
  NCDataset("foo$i.nc","c") do ds
    defVar(ds,"data",[10., 11., 12., 13.], ("lon",))
  end
end

ds = NCDataset(["foo$i.nc" for i = 1:3],aggdim = "sample", isnewdim = true)
size(ds["data"])
# output
# (4, 3)
```
