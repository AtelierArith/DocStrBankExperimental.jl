```
isisomorph(tree1::CladoTree, tree2::CladoTree) :: Bool
isisomorph(tree1::ChronoTree, tree2::ChronoTree) :: Bool
```

2つの木が同型であるかをテストします。

両方の系統樹が日付付きの場合、同型性は枝の長さが対応して等しいことを意味します。それ以外の場合は、木のトポロジーのみが比較されます。
