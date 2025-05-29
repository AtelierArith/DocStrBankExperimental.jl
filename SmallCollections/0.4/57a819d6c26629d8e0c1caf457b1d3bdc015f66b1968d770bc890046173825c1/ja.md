```
push(s::S, xs...) where S <: SmallBitSet -> S
```

`s`に他の引数`xs`を追加することによって得られる`SmallBitSet`を返します。

`Base.push!`、`BangBang.push!!`も参照してください。
