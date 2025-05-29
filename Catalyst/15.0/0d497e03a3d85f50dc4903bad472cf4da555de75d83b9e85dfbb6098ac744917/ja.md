```
@compound
```

複合種を作成するマクロで、これはより小さな構成種から構成されています。

例:

```julia
t = default_t()
@species C(t) O(t)
@compound CO2(t) ~ C + 2O
```

注意:

  * 構成種は `@compound` マクロを使用する前に定義されている必要があります。
