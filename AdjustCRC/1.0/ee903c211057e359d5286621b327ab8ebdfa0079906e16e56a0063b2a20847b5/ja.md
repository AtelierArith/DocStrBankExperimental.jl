```
adjust_crc!(crc, a::AbstractVector{UInt8}, wantcrc::UInt32, fixpos::Integer)
```

`a[fixpos:fixpos+3]` に 4 バイトを書き込んで、`crc(a)` が `wantcrc` と等しくなるようにします。これは、データのチェックサムを *データ内* に保存したい場合や、単に crc を任意の事前に決定された値に設定したい場合に特に便利です。ここで、`crc` は 32 ビットの CRC チェックサムを計算する関数であり、`CRC32c` 標準ライブラリの `crc32c` または [CRC32.jl パッケージ](https://github.com/JuliaIO/CRC32.jl) の `crc32` のいずれかです。

`adjust_crc!` 関数は、`fixpos` が配列 `a` の末尾に近い場合に最も効率的であり、`fixpos` が先頭に近い場合は最も遅くなります。（ただし、すべてのケースでコストは `length(a)` に対して線形にスケールするはずです。）ファイルや I/O ストリームの末尾に類似のパディングバイトを追加する [`adjust_crc`](@ref) も参照してください（これは、ファイル全体を一度にメモリに読み込む必要がないという利点があります）。
