```
@capture ex pattern
```

`Rule`オブジェクトを使用して、`pattern`に一致する場合に式をキャプチャします。`pattern`が一致する場合は`true`を返し、スロット変数のマッチ結果を呼び出しスコープに注入します。それ以外の場合はfalseを返します。`pattern`を指定するためのルール言語は、`@capture`と`@rule`で同じです。

```julia
julia> @syms a; ex = a^a;

julia> if @capture ex (~x)^(~x)
           @show x
       elseif @capture ex 2(~y)
           @show y
       end;
x = a
```

参照: [`@rule`](@ref)
