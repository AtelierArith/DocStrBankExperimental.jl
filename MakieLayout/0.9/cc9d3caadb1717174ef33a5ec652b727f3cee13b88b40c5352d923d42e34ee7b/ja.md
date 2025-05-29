```
tightlimits!(la::LAxis, sides::Union{Left, Right, Bottom, Top}...)
```

指定されたすべての側面の自動制限マージンをゼロに設定します。

例:

```
tightlimits!(laxis, Bottom())
```
