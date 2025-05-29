```
remove_hydrogens!(q::MolGraph) -> Nothing
```

分子クエリから水素を削除します。

`specialize_nonaromatic!`の後に適用する必要があります。この関数は、PubChemデータセットにおけるPAINSクエリの一般化を目的としています。
