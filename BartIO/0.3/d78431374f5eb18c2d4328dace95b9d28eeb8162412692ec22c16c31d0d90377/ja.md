```
read_cfl(filename::String)
```

  * read_cfl(filename(no extension)) -> Array{ComplexF32,N} where N is defined the filename.hdr file
  * read_cfl(filename.cfl) -> Array{ComplexF32,N} where N is defined the filename.hdr file
  * read_cfl(filename.hdr) -> Array{ComplexF32,N} where N is defined the filename.hdr file

Berkeley Advanced Reconstruction Toolbox (BART)によって作成されたファイルから複素データを読み込みます。出力は、.hdrファイルに保存された次元を持つComplexF32の配列です。

## パラメータ:

  * filename:   cflおよびhdrファイルのパスとファイル名。拡張子なし、.cflで終わる、または.hdrで終わることができます。
