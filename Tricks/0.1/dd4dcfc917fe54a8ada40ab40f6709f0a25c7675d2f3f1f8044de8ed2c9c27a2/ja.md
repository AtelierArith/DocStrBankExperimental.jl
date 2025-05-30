```
static_method_count(f, [type_tuple::Type{<:Tuple])
static_method_count(@nospecialize(f)) = _static_methods(Main, f, Tuple{Vararg{Any}})
```

`length(methods(f, tt))`を返しますが、コンパイル時に実行され（worldage引数は受け付けません）。
