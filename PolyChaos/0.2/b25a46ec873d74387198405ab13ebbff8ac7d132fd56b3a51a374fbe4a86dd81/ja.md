**単変量**

```
var(x::AbstractVector,op::AbstractOrthoPoly)
var(x::AbstractVector,t2::Tensor)
```

**多変量**

```
var(x::AbstractVector,mop::MultiOrthoPoly)
var(x::AbstractVector,t2::Tensor)
```

PCE `x` を持つ確率変数の分散を計算します。
