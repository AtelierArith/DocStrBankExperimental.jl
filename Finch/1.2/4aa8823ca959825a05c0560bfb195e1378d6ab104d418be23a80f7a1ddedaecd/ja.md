```
fwrite(filename::AbstractString, tns::Finch.Tensor)
```

Finchテンソルをファイルに書き込みます。ファイル形式はファイル拡張子によって決まります。サポートされているファイル拡張子は次のとおりです：

  * `.bsp.h5`: [Binsparse](https://github.com/GraphBLAS/binsparse-specification) HDF5ファイル形式
  * `.bspnpy`: [Binsparse](https://github.com/GraphBLAS/binsparse-specification) NumPyおよびJSONサブディレクトリ形式
  * `.mtx`: [MatrixMarket](https://math.nist.gov/MatrixMarket/formats.html#MMformat) `.mtx` テキストファイル形式
  * `.ttx`: [TensorMarket](https://github.com/willow-ahrens/TensorMarket.jl) `.ttx` テキストファイル形式
  * `.tns`: [FROSTT](http://frostt.io/tensors/) `.tns` テキストファイル形式
