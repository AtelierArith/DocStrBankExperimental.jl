```
is_zero_cycle(n, d, m, P)
```

`P`がモジュライ空間の0サイクルである場合は`true`を返し、それ以外の場合は`false`を返します。

# 引数

  * `n::Int64`: 射影空間の次元。
  * `deg::Int64`: 安定写像の次数。
  * `n_marks::Int64`: マークの数。
  * `P`: 同変クラス。

# 例

```julia-repl
julia> P = Hypersurface(g,c,w,s,5);
julia> is_zero_cycle(4,1,0,P)
true
```
