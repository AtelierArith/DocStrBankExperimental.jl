```
mapsubtrees(f, t::FileTree, pattern::Union{GlobMatch, Regex})
```

提供されたパターンに一致するすべてのノードに対して、関数 `f` を適用します。

`f` が `File` または `FileTree` を返す場合、この新しいノードは一致したノードに置き換えられます。

`f` が `nothing` を返す場合、一致したノードは削除されます。

`f` が他の値を返す場合、その値はノードの値として使用され、ノード自体は子を空にされます。

これにより、複雑なユースケースに対して `mapsubtrees` を使用することができます。

サブディレクトリの値を `hcat` 関数で結合し、その値を `vcat` で結合したい場合、`mapsubtrees` を使用してこれを達成できます：

デモは以下の通りです：

```julia
t = maketree("dir"=>([string(j)=>[(name=string(i), value=(i,j)]
                        for i=1:2] for j=1:3]

t1 = mapsubtrees("*") do subtree
    reducevalues(vcat, subtree)
end
```

```julia
reducevalues(hcat, t1)
```
