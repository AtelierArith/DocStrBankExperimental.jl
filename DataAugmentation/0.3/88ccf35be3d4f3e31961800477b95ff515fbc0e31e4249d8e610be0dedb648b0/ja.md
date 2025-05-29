```
apply!(buffer::I, tfm, item::I)
```

`tfm`を`item`に適用し、事前に割り当てられた`buffer`を変更します。

`buffer`は`buffer = makebuffer(tfm, item)`で取得できます。

```
apply!(buffer, tfm::Transform, item::I; randstate) = apply(tfm, item; randstate)
```

デフォルトは`apply(tfm, item)`（非変更版）です。
