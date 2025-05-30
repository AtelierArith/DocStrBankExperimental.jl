```
prepend!(node.children::NodeChildren, children) -> NodeChildren
```

`node`の子供のリストの先頭に、イテラブル`children`のすべての要素を追加します。`children`のいずれかが別の木の一部である場合、それらは最初にその木からリンク解除されます（[`unlink!`](@ref）を参照）。子供に対するイテレータを返します。

!!! warning "prepend中のエラー"
    この操作は原子ではなく、`prepend!`中のエラー（例えば、`children`に間違った型の要素が含まれている場合）は、新しい子供の部分的なprependを引き起こす可能性があります。これは、配列に対する`append!`の動作に似ています（[JuliaLang/julia#15868](https://github.com/JuliaLang/julia/issues/15868）を参照）。

