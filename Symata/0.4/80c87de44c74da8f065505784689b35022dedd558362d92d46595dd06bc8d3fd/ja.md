```
mxpra(head, args::MxprArgs)
```

`head` と引数 `args` を持つ Symata 式を作成します。引数はコピーされません。`head` がシンボルの場合は `Mxpr{head}` 型のオブジェクトが返され、それ以外の場合は `Mxpr{GenHead}` 型のオブジェクトが返されます。型 `MxprArgs` は現在 `Array{Any,1}` のエイリアスであり、関数 `newargs()` でインスタンス化できます。
