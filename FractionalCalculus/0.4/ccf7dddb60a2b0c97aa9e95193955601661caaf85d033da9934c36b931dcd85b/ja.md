# グリュンワルド・レティニコフ意味の三点補間

```
fracdiff(f, α, end_point, h, GLLagrangeThreePointInterp())
```

ラグランジュ三点補間を使用して分数導関数を近似します。

### 例

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.006, GLLagrangeThreePointInterp())
1.1261297605404632
```
