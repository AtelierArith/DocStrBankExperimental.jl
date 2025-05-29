```
fread(filename::AbstractString)
```

ファイル拡張子によって決定されるファイル形式を使用して、ファイルからFinchテンソルを読み込みます。サポートされているファイル拡張子は次のとおりです：

  * `.bsp.h5`: [Binsparse](https://github.com/GraphBLAS/binsparse-specification) HDF5ファイル形式
  * `.bspnpy`: [Binsparse](https://github.com/GraphBLAS/binsparse-specification) NumPyおよびJSONサブディレクトリ形式
  * `.mtx`: [MatrixMarket](https://math.nist.gov/MatrixMarket/formats.html#MMformat) `.mtx` テキストファイル形式
  * `.ttx`: [TensorMarket](https://github.com/willow-ahrens/TensorMarket.jl) `.ttx` テキストファイル形式
  * `.tns`: [FROSTT](http://frostt.io/tensors/) `.tns` テキストファイル形式
