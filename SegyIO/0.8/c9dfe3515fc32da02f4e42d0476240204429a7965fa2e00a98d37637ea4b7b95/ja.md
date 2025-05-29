```
scan_file(file::String, keys::Array{String, 1};
          chunksize::Int = CHUNKSIZE,
          verbosity::Int = 1)
```

`file`を`keys`のヘッダーフィールドのためにスキャンし、トレースの単一ソースグループ内のメタデータ要約を含むSeisConオブジェクトを返します。`file`の`chunksize` MBを一度にメモリにロードします。

# 例

```
s = scan_file('testdata.segy', ["SourceX", "SourceY"])
```
