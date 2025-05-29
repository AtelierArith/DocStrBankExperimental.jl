```
N = node(f::Function, args...)
```

静的操作 `f` と引数 `args` をラップする `Node` オブジェクト `N` を定義します。`args` の `n` 要素の各々は `Node` または `Source` オブジェクトでなければなりません。ノード `N` は以下の呼び出し動作を持ちます：

```
N() = f(args[1](), args[2](), ..., args[n]())
N(rows=r) = f(args[1](rows=r), args[2](rows=r), ..., args[n](rows=r))
N(X) = f(args[1](X), args[2](X), ..., args[n](X))
```
