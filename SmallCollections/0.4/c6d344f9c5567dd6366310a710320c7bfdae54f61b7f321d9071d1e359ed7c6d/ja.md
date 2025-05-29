```
delete(s::S, x) where S <: SmallBitSet -> S
```

`s`が`x`を含む場合、その要素を削除した集合を返します。そうでない場合は`s`を返します。

関連情報として`Base.delete!`、`BangBang.delete!!`を参照してください。
