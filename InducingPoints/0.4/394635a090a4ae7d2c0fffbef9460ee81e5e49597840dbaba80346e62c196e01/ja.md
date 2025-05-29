```
UniformGrid{T,Titer} <: AbstractVector{T}
```

`Iterators.ProductIterator`のラッパーを表すメモリ効率の良いカスタムオブジェクトです。ブロードキャスティングやその他の関連する配列メソッドをサポートし、グリッド上のすべてのポイントを明示的に計算することを避けます。
