```
BGZFCompressorStream(io::IO; threads=nthreads(), compresslevel=6)
```

基になる `io` からデータをブロック gzip 圧縮し、指定された `compresslevel` で `TranscodingStream` を作成します。このストリームは、最大 `threads` ブロックを同時に圧縮します。
