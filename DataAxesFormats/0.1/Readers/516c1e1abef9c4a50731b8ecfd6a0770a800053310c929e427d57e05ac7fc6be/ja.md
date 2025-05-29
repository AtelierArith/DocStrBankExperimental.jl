```
vector_version_counter(daf::DafReader, axis::AbstractString, name::AbstractString)::UInt32
```

ベクトルのバージョン番号を返します。これは、[`set_vector!`](@ref DataAxesFormats.Writers.set_vector!), [`empty_dense_vector!`](@ref DataAxesFormats.Writers.empty_dense_vector!) または [`empty_sparse_vector!`](@ref DataAxesFormats.Writers.empty_sparse_vector!) が呼び出されるたびにインクリメントされます。これは、データのコピーを最小限に抑えるために、他のプログラミング言語へのインターフェースによって使用されます。

!!! note
    これはインスタンスごとの純粋なメモリ内であり、**グローバルな永続バージョンカウンターではありません**。つまり、永続的なディスク `daf` データセットを開いても、バージョンカウンターはゼロから始まります。

