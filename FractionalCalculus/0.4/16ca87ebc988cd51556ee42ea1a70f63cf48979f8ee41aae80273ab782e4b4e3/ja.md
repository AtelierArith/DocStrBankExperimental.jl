# リーマン・リウビル意味の分数積分近似

```
fracint(f, α, end_point, h, RLIntApprox())
```

### 例

```julia-repl
julia> fracint(x->x^5, 0.5, 2.5, 0.0001, RLIntApprox())
64.36229646291393
```

**階段近似**を使用して元の関数を近似し、総和を実装します。
