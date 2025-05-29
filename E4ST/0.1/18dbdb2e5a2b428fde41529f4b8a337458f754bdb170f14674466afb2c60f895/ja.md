```
mod_rank(::Type{Modification}) ->
```

Modificationのランクを返します。ランクは、他のタイプのmodに対してmodのタイプを適用すべき順序です。デフォルトは0で、1は他のmodの後に、-1は前に来ることを意味します。ランクはmodタイプに対して定義されています。
