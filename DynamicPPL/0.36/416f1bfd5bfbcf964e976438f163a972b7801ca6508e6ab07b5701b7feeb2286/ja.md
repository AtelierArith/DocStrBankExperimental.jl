```
empty!!(vi::AbstractVarInfo)
```

`vi.metadata`のフィールドを空にし、`vi.logp[]`と`vi.num_produce[]`をゼロにリセットします。

これは、空の`vi`を前提とするサンプリングアルゴリズム（例：`SMC`）を使用する際に便利です。
