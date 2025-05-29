```
reducevalues(f, t::FileTree; associative=true, init=nothing)
```

ツリー内の値を結合するために `f` を使用します。

  * `associative=true` は `f` が結合的に適用できると仮定します
  * `init` キーワード引数はファイルツリーが空の場合に返されます。`init` が提供されていない場合、空のツリーに対して reduce を行うとエラーが発生します
