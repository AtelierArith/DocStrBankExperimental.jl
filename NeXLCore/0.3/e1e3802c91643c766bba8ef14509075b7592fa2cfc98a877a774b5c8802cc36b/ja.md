```
atoms_per_cm³(mat::Material, elm::Element) =
```

指定された材料における指定された元素の cm³ あたりの原子数。材料は `:Density` プロパティを定義している必要があります。

```
atoms_per_cm³(mat::Material)
```

mat 内のすべての元素の cm³ あたりの原子の総数。
