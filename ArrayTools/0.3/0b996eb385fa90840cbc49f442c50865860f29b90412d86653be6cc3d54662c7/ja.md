```
MaybeArrayAxes{N}
```

は、配列の軸を指定するために適格な引数の型であり、`MaybeArrayAxis`の`N`タプルです。

`as_array_axes(x::MaybeArrayAxes{N})`を呼び出すと、`ArrayAxes{N}`のインスタンスが得られることが保証されています。
