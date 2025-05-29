```
SingletonVector(itr) :: AbstractVector
SingletonVector{T}(itr) :: AbstractVector{T}
```

シングルトンベクトルを作成します。イテレータ `itr` は1つだけの要素を持たなければなりません。

コンストラクタ `SingletonVector(itr)` は、`IteratorEltype(itr)` が `HasEltype` の場合、`eltype(itr)` を使用します。
