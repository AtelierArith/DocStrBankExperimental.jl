# リーマン・リウヴィル意味の分数積分を分数シンプソンの公式を用いて近似する。

### 例

```julia-repl
julia> fracint(x->x, 0.5, 1, 0.000001, RLIntSimpson())
0.7516516520541335
```

```tex
@inproceedings{Li2015NumericalMF,
  title={Numerical Methods for Fractional Calculus},
  author={Changpin Li and Fanhai Zeng},
  year={2015}
}
```

分数シンプソンの公式を用いて離散分数積分を行う。
