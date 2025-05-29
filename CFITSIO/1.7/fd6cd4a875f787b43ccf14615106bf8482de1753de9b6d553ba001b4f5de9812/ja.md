```
fits_read_imghdr(f::FITSFile, maxdim::Integer = 99)
```

画像HDUのヘッダーを読み込みます。ここで、`maxdim`は読み込む最大次元数を表します。デフォルトでは、`maxdim == 99`は画像のすべての次元に沿ったサイズを読み込みます。この関数は、`SIMPLE::Bool`、`BITPIX::Int`、`NAXIS::Int`、`NAXES::Vector{Int}`、`PCOUNT::Int`、`GCOUNT::Int`、および`EXTEND::Bool`の値を返します。`NAXES`の長さは`min(NAXIS, maxdim)`に設定されます。

`BITPIX`の値は画像のデータ型を示し、[`type_from_bitpix`](@ref)関数を使用してJulia型に変換できます。

!!! note
    `PCOUNT`は通常画像HDUに対して`0`であり、`GCOUNT`は通常最新のファイルに対して`1`です。

