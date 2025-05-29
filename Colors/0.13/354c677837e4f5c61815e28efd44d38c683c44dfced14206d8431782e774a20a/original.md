```
DE_94(kl=1, kc=1, kh=1, k1=0.045, k2=0.015)
```

Construct a metric of CIE Delta E 94 recommendation (1994), with weighting parameters `kl`, `kc`, `kh`, `k1`, and `k2` as provided for in the recommendation. The `kl`, `k1`, and `k2` depend on the application:

|      | Graphic Arts | Textiles |
|:----:|:------------ |:-------- |
| `kl` | `1`          | `2`      |
| `k1` | `0.045`      | `0.048`  |
| `k2` | `0.015`      | `0.014`  |

and the default values are for graphic arts. The `kc` and `kh` default to `1`.

The `DE_94` is more perceptually uniform than the [`DE_AB`](@ref), but has some non-uniformities resolved by the [`DE_2000`](@ref).

!!! note
    The `DE_94` is a quasimetric, i.e. violates symmetry. Therefore, `colordiff(a, b, metric=DE_94())` may not equal to `colordiff(b, a, metric=DE_94())`. The first argument of `colordiff` is taken as the reference (standard) color.

