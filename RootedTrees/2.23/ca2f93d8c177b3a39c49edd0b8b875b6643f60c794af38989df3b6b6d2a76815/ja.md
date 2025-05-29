```
SubtreeIterator(t::AbstractRootedTree)
```

根付き木 `t` の [`subtrees`](@ref) の遅延イテレータ表現。[`RootedTreeIterator`](@ref) と同様に、イテレーション中にそれらを保存または変更したい場合は、イテレートを `copy` する必要があります。なぜなら、それらは内部キャッシュへのビューである可能性があるからです。
