```
TreeIterator{T}
```

AbstractTreesインターフェースを実装する木のイテレータです。すべての`TreeIterator`は、イテレーションの状態を完全に決定し、[`next`](@ref)を使用して独自の代替プロトコルを実装する[`IteratorState`](@ref)のラッパーに過ぎません。

## コンストラクタ

すべての`TreeIterator`は、`T(node)`という1引数のコンストラクタを持ち、`node`からイテレーションを開始します。
