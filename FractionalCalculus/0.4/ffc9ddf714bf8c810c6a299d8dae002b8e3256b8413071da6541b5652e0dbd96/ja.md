# リーマン・リウビル意味の分数積分 **線形補間** を使用して。

```
fracint(f, α, end_point, h, RLLinearInterp())
```

### 例

```julia-repl
julia> fracint(x->x^5, 0.5, 2.5, 0.0001, RLLinearInterp())
64.36234206434942
```

**RLLinearInterp** は *RLIntApprox* と比較してより複雑ですが、より正確です。

$$
f_{j+1}
$$

と $f_j$ の間の [線形補間](https://en.wikipedia.org/wiki/Linear_interpolation) を展開することで、**RLLinearInterp** メソッドは **RLIntApprox** よりも正確です。
