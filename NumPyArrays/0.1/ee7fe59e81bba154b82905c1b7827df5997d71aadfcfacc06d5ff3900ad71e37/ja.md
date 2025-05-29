```
NumPyArray{T,N}(po::PyObject)
```

NumPyArrayはPyCall.PyArrayのラッパーです。これはAbstractArrayです。NumPyArrayの主な目的は、Julia配列をNumPyArraysに変換するためのコンストラクタを提供することです。`T`は配列の要素型です。`N`は次元の数です。

NumPyから既存の配列をラップするなどの他の用途には、`PyCall.PyArray`を使用してください。

`NumPyArray`をそれらの型に変換するには、`PyObject`および`PyArray`メソッドを使用してください。
