# リーマン・リウヴィル意味の分数積分を分数台形公式を用いて近似する。

### 例

```julia-repl
julia> fracint(x->x, 0.5, 1, 0.001, RLIntTrapezoidal())
0.7522527780636226
```

《分数微積分の数値的方法》。台形法を用いて分数積分を近似する。
