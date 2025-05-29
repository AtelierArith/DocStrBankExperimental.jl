```
user_registered_functions(model::InfiniteModel)::Vector{RegisteredFunction}
```

`model` にユーザーが登録したすべての関数（およびそれに関連する情報）を返します。各関数は [`RegisteredFunction`](@ref) として保存されています。
