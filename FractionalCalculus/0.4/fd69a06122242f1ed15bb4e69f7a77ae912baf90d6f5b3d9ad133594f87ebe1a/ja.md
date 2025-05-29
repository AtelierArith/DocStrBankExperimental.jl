# ハダマード感覚台形近似アルゴリズム

```
fracdiff(f, α, a, x, h, HadamardTrap())
```

**台形公式**の有限部分積分を使用して、分数ハダマード導関数を計算します。

### 例

```julia-repl
julia> fracdiff(x->x, 0.5, 0, 1, 0.001, HadamardTrap())
0.9738507879228328
```
