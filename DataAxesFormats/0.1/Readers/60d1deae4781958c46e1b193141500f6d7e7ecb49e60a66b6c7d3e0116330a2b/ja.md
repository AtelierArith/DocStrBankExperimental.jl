```
axis_version_counter(daf::DafReader, axis::AbstractString)::UInt32
```

軸のバージョン番号を返します。これは、[`delete_axis!`](@ref DataAxesFormats.Writers.delete_axis!) が呼び出されるたびにインクリメントされます。他のプログラミング言語とのインターフェースでデータのコピーを最小限に抑えるために使用されます。

!!! note
    これはインスタンスごとの純粋なメモリ内であり、**グローバルな永続バージョンカウンタ**ではありません。つまり、永続的なディスク `daf` データセットを開いても、バージョンカウンタはゼロから始まります。

