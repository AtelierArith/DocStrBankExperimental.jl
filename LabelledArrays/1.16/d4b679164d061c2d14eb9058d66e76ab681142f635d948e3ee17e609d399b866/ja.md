```
LVector(v1::Union{SLArray,LArray}; kwargs...)
```

v1の1Dコピーを作成し、kwargs内の対応するアイテムを置き換えます。

例えば：

```
z = LVector(a=1, b=2, c=3);
z2 = LVector(z; c=30)
```
