```
Z = opExtension(I, ncol)
Z = opExtension(:, ncol)
```

ベクトルのサイズ `length(I)` を `ncol` に拡張する LinearOperator を作成します。新しいベクトル上の要素の位置はインデックス `I` によって与えられます。操作 `w = Z * v` は `w = zeros(ncol); w[I] = v` と同等です。

```
Z = opExtension(k, ncol)
```

`opExtension([k], ncol)` のエイリアスです。
