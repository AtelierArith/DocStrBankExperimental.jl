```
isclosedform(b::Transform)::bool
isclosedform(b⁻¹::Inverse{<:Transform})::bool
```

`b`の評価が閉じた形式の実装を持つかどうかに応じて、`true`または`false`を返します。

ほとんどの変換は閉じた形式の評価を持っていますが、そうでない場合もあります。たとえば、`PlanarLayer`の*逆*評価は、評価するために反復手順を必要とします。
