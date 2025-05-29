```
codim(n, d, m, P)
```

同変クラス `P` のコディメンション。

# 引数

  * `n::Int64`: 射影空間の次元。
  * `d::Int64`: 安定写像の次数。
  * `m::Int64`: マークの数。
  * `P`: 同変クラス。

# 例

```julia-repl
julia> P = Hypersurface(g,c,w,s,5);
julia> codim(4,1,0,P)
6
```
