```
scan_file(file::String, keys::Array{String, 1}, blocksize::Int;
          chunksize::Int = CHUNKSIZE,
          verbosity::Int = 1)
```

`file`を`keys`のヘッダーフィールドのためにスキャンし、`blocksize`のトレースのグループにメタデータの要約を含むSeisConオブジェクトを返します。`file`から`chunksize` MBを一度にメモリにロードします。

`file`内のトレースの数が`blocksize`で割り切れない場合、最後のブロックは残りのトレースを要約します。

`verbosity`を0に設定すると、スキャン中の現在のファイルに関する更新が抑制されます。

# 例

```
s = scan_file('testdata.segy', ["SourceX", "SourceY"], 300)
```
