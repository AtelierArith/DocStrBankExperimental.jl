```
mweight(x::Vector)
```

ベクトル `w = x / sum(x)` を含む `Weight` 型のオブジェクトを返します（ad'hoc ビルディングの場合、`w` は 1 に合計される必要があります）。

## 例

```julia
using Jchemo

x = rand(10)
w = mweight(x)
sum(w.w)
```
