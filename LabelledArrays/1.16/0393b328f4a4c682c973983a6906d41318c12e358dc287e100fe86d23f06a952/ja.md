```
SLVector(v1::SLArray; kwargs...)
```

v1の1Dコピーを作成し、kwargs内の対応するアイテムを置き換えます。

例えば：

```
z = SLVector(a=1, b=2, c=3);
z2 = SLVector(z; c=30)
```
