```
prev(list, state) -> item, prevstate
```

`list`から現在のアイテムを返し、状態を前のエントリを指すように設定します。次のことが成り立ちます。

```
_, p = prev(list, s)
_, n = next(list, p)
n == s
```
