```
xb,ll = smooth(pf, M, u, y, p=parameters(pf))
xb,ll = smooth(pf, xf, wf, wef, ll, M, u, y, p=parameters(pf))
```

前方フィルタリングと後方シミュレーションを使用して粒子スムージングを実行します。スムーズな粒子と対数尤度を返します。詳細については、[`smoothed_trajs`](@ref)、[`smoothed_mean`](@ref)、[`smoothed_cov`](@ref)を参照してください。
