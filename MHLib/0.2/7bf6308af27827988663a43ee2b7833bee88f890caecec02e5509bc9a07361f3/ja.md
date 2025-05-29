```
obj(s::Solution)
```

`obj_val_valid`の場合は`s.obj_val`を返し、そうでなければ`objective(::Solution)`を使って計算します。
