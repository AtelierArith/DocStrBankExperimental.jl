```
sig = signature(sigsv::SimpleVector)
```

適切な `SimpleVector` からメソッドシグネチャを計算します：`sigsv[1]` はシグネチャを保持し、`sigsv[2]` は `TypeVar` を保持します。

# 例：

`f(x::AbstractArray{T}) where T` の場合、対応する `sigsv` は次のように構築されます。

```
T = TypeVar(:T)
sig1 = Core.svec(typeof(f), AbstractArray{T})
sig2 = Core.svec(T)
sigsv = Core.svec(sig1, sig2)
sig = signature(sigsv)
```
