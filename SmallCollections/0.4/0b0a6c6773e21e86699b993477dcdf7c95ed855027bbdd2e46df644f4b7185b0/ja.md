```
pop(s::S, x, default::T) where S <: SmallBitSet -> Tuple{S, Union{Int,T}}
```

`s`が`x`を含む場合、`t`が`x`を削除した集合`s`であるペア`(t, x)`を返します。そうでない場合は`(s, default)`を返します。

他にも`Base.pop!`、`BangBang.pop!!`を参照してください。
