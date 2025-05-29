```
abstract type HierarchicalSelection <: Selection end
```

サブ選択の概念を持つ選択のための抽象型。

```
get_subselections(selection::HierarchicalSelection)
```

関連するアドレスとサブ選択のペアに対するイテレータを返します。
