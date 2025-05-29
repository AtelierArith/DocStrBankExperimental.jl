```
gif_mcmc_ising2d(S=nothing, E=nothing, M=nothing;
    s=rand_ising2d(), k=1.0, β=k*β_ising2d, rng=default_rng(),
    algorithm=default_algorithm(), progress=true,
    nwarmups=1000, nskips=1000, niters=500,
    ylim_E=(-1.55, -1.30), ylim_M=(-0.8, 0.8), lw=1.0, alpha=0.8,
    gifname="ising2d_mcmc.gif", fps=10,
    size=(600, 300), color=:gist_earth, clim=(-2, 1.1), kwargs...
)
```

は、サイトごとのエネルギーと磁化を持つ2Dイジングモデルのgifアニメーションを作成します。

例:

```
gif_mcmc_ising2d()
```
