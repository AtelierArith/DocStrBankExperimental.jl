```
AbstractBody
```

浸漬体の抽象型。任意の `AbstractBody` サブタイプは次を実装しなければなりません。

```
d = sdf(body::AbstractBody, x, t=0)
```

および

```
d,n,V = measure(body::AbstractBody, x, t=0, fastd²=Inf)
```

ここで `d` は時刻 `t` における `x` から体までの符号付き距離であり、`n` と `V` は `x` で暗示される法線ベクトルと速度ベクトルです。高速近似法は、`d^2>fastd²` の場合に `≈d,zero(x),zero(x)` を返すことができます。
