```
EmptyVector() :: AbstractVector{Union{}}
EmptyVector(itr) :: AbstractVector
EmptyVector{T}() :: AbstractVector{T}
EmptyVector{T}(itr) :: AbstractVector{T}
```

空のベクターを作成します。 イテレータ `itr` は空でなければなりません。

単項コンストラクタ `EmptyVector(itr)` と `EmptyVector{T}(itr)` は、イテレータ `itr` が空であることを確認します。 コンストラクタ `EmptyVector(itr)` は、`IteratorEltype(itr)` が `HasEltype` の場合、`eltype(itr)` を使用します。
