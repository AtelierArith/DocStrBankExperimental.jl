```
collect_structarray(itr; initializer = default_initializer)
```

`itr`を`StructArray`に集めます。ユーザーはオプションで`initializer`を渡すことができ、これは型とサイズに対して`S`のeltypeとサイズ`d`の配列を関連付ける関数`(S, d) -> v`です。デフォルトでは`initializer`は`Array`の`StructArray`を返しますが、カスタム配列型を使用することもできます。
