```
BGZFDecompressorStream(io::IO; threads=nthreads())
```

基になる `io` からブロック gzip 圧縮データを解凍する `TranscodingStream` を作成します。このストリームは、最大 `threads` ブロックを同時に圧縮します。
