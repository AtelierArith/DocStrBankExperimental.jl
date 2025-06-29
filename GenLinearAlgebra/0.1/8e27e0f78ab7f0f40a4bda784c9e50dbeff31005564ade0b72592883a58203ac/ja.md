`permanent(m)`

は、正方行列 `m` の *permanent* を返します。これは $\sum_{p\in\frak S_n}\prod_{i=1}^n m[i,p(i)]$ によって定義されます。

permanent の定義が行列式の定義と似ていることに注意してください。実際、唯一の違いは置換の符号が欠けていることです。しかし、permanent は行列式とはかなり異なり、例えば多重線形でも交代的でもありません。ただし、重要な組合せ論的性質を持っています。

```julia-repl
julia> permanent([0 1 1 1;1 0 1 1;1 1 0 1;1 1 1 0]) # 1:4 の derangements の数を計算する非効率的な方法
9

julia> permanent([1 1 0 1 0 0 0; 0 1 1 0 1 0 0;0 0 1 1 0 1 0; 0 0 0 1 1 0 1;1 0 0 0 1 1 0;0 1 0 0 0 1 1;1 0 1 0 0 0 1]) # 順序 2 の射影平面に適合する 24 の置換 
24 
```
