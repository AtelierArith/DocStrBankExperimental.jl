```
create_mlp(
    ninput::Int, 
    noutput::Int, 
    hiddenlayers::Tuple{Vararg{Int}}, 
    dropoutp::Union{<:AbstractFloat,Tuple{Vararg{<:AbstractFloat}}}
    )
```

`mlp`を返します。`ninput`/`noutput`は入力/出力チャネルの数であり、各層のユニット数は`hiddenlayers`で指定されます。`dropoutp`はドロップアウト層のドロップアウト確率を含みます。これは単一の値（出力の前に1つのドロップアウト層）または隠れ層と同じ長さであることができます。
