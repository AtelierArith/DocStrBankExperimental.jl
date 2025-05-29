ChunkedFillArray(v::T, size, chunksize) は、値 `v` を持つ遅延フィル配列を構築します。この配列は、サイズ `size` の n 次元で、サイズ `chunksize` のチャンクを持つチャンク化された DiskArray のように振る舞います。
