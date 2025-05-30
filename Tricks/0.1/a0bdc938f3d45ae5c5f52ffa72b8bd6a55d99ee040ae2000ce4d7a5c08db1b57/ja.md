```
static_methods(f, [type_tuple::Type{<:Tuple])
static_methods(@nospecialize(f)) = _static_methods(Main, f, Tuple{Vararg{Any}})
```

`methods`のようですが、コンパイル時に実行され（worldage引数を受け付けません）。
