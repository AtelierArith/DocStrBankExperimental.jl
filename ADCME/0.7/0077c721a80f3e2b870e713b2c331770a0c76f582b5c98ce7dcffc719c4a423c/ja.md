```
independent(o::PyObject, args...; kwargs...)
```

`o`を返しますが、勾配を計算する際、上位の勾配は`o`の依存変数には逆伝播されません。
