```
(T::TorQuadModule)(v::Vector) -> TorQuadModuleElem
```

`v`を`T`に強制変換します。

`T = M/N`の場合、これは`v`が`M`の周囲空間に存在し、$v \in M$であることを前提としています。
