# カプート感覚の区分的アルゴリズム

```
fracdiff(f, α, end_point, h, CaputoTrap())
```

区分線形補間関数を使用して入力関数を近似し、カプート微分を組み合わせて合計を実装します。

### 例

```julia-repl
julia> fracdiff(x->x^5, 0.5, 2.5, 0.001, CaputoTrap())
```

点 $x=2.5$ における $f(x)=x^5$ の分数微分を返します。

```tex
@article{LI20113352,
title = {Numerical approaches to fractional calculus and fractional ordinary differential equation},
author = {Changpin Li and An Chen and Junjie Ye},
}
```
