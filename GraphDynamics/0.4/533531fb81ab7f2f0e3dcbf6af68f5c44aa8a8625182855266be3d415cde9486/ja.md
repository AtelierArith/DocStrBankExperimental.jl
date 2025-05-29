```
isstochastic(::Type{T})
```

デフォルトは `false` ですが、確率微分方程式を定義するサブシステムの場合、この関数に次の形式のメソッドを追加する必要があります。

```
GraphDynamics.isstochastic(::Type{Mytype}) = true
```
