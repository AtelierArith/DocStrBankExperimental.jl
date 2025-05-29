```
sample(::Type{NodeLoc}, root::RuleNode, maxdepth::Int=typemax(Int))
```

最大深さがmaxdepthを超えないように木の中から一様にランダムなノードを選択します。サブツリーを置き換えられるように親を使用して位置を指定するNodeLocを返します。
