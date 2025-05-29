```
thiran(τ::Real, Ts)
```

潜在的な分数遅延 $τ$ をサンプル時間 `Ts` の Thiran 全通フィルタとして離散化します。

Thiran 全通フィルタは、最大平坦な群遅延を提供します。

$$
τ
$$

が $Ts$ の整数倍である場合、Thiran 全通フィルタは $z^{-τ/Ts}$ に簡略化されます。

参考文献: T. I. Laakso, V. Valimaki, M. Karjalainen and U. K. Laine, "Splitting the unit delay [FIR/all pass filters design]," in IEEE Signal Processing Magazine, vol. 13, no. 1, 1996. ```
