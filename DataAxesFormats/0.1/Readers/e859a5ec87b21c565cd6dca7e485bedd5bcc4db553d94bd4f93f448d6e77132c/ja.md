```
matrix_version_counter(
    daf::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString
)::UInt32
```

行列のバージョン番号を返します。軸の順序は重要ではありません。これは、[`set_matrix!`](@ref DataAxesFormats.Writers.set_matrix!), [`empty_dense_matrix!`](@ref DataAxesFormats.Writers.empty_dense_matrix!) または [`empty_sparse_matrix!`](@ref DataAxesFormats.Writers.empty_sparse_matrix!) が呼び出されるたびにインクリメントされます。他のプログラミング言語へのインターフェースによってデータのコピーを最小限に抑えるために使用されます。

!!! note
    これはインスタンスごとの純粋なメモリ内であり、**グローバルな永続バージョンカウンター**ではありません。つまり、永続的なディスク `daf` データセットを開いても、バージョンカウンターはゼロから始まります。

