```
MtlArray{T,N,S} <: AbstractGPUArray{T,N}
```

`N`次元のMetal配列で、ストレージモードは`S`、要素の型は`T`です。

`S`は`Metal.PrivateStorage`（デフォルト）、`Metal.SharedStorage`、または`Metal.ManagedStorage`のいずれかです。

詳細については、Metal.jlのドキュメントの配列プログラミングセクションを参照してください。
