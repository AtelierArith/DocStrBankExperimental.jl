`CPoset(f::Function,n::integer)`

は、関数 `f` によって与えられた順序で `1:n` の `Poset` を作成します。

```julia-repl
julia> CPoset((x,y)->y%x==0,8)  # 除算のポセット
1<5,7
1<2<4<8
1<3<6
2<6
```
