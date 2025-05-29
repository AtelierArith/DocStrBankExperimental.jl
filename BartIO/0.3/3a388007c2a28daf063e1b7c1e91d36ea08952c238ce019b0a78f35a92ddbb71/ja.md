```
write_cfl(filename::String,dataCfl::Array{ComplexF32})
```

  * write_cfl(filename(no extension),Array{ComplexF32})
  * write_cfl(filename.cfl, Array{ComplexF32})
  * write_cfl(filename.hdr,Array{ComplexF32})

複素データをバークレー高度再構成ツールボックス（BART）の規約に従ってファイルに書き込みます。入力は、.hdrファイルに保存された次元を持つComplexF32の配列です。

## パラメータ:

  * filename:   cflおよびhdrファイルのパスとファイル名で、拡張子なし、.cflで終わる、または.hdrで終わることができます。
  * Array{ComplexF32,N}:   画像/k空間に対応するComplexF32の配列
