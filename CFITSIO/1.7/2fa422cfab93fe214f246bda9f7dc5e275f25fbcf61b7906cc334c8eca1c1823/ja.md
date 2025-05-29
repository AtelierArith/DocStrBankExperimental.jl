```
fits_create_binary_tbl(f::FITSFile, numrows::Integer,
                       coldefs::Union{Array{NTuple{3,String}}, Array{NTuple{2,String}}},
                       extname::Union{String, Nothing} = nothing)
```

新しいHDUにバイナリテーブルを含む新しいHDUを追加します。パラメータの意味は、[`fits_create_ascii_tbl`](@ref)の呼び出しと同じです。

一般的に、新しいHDUにテーブルを作成するためにはこの関数を選択すべきです。バイナリテーブルはディスク上で占めるスペースが少なく、読み書きがより効率的です。（さらに、いくつかのデータ型はASCIIテーブルではサポートされていません）。
