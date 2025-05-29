```
all_arm_indices(reward)
```

与えられた報酬のためのアームインデックスのリストを返します。たとえば、アームのベクトルの場合、そのベクトル内のインデックスのリストを返します：各インデックスはアームに関連付けられています。

```
all_arm_indices(instance::CombinatorialInstance{T}) where T
```

与えられた組合せインスタンスのためのアームインデックスのリストを返します。
