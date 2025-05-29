# ハダマール感覚右矩形近似アルゴリズム

```
fracdiff(f, α, a, x, h, HadamardTrap())
```

**右矩形公式**の有限部分積分を使用して、分数ハダマール導関数を計算します。

### 例

```julia-repl
julia> fracdiff(x->x, 0.5, 0, 1, 0.001, HadamardRRect())
0.9738507879228337
```
