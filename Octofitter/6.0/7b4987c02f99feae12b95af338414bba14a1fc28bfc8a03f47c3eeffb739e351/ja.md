```
octoplot(
    system::Octofitter.Model,
    chain::MCMCChains.Chains;
    fname="$(system.name)-plot-grid",
    color = "$(first(keys(system.planets)))_e",
    colorbartitle=string(color),
    clims = quantile(vec(chain[color]),(0.01, 0.99)),
    cmap = :plasma,
    dpi=200,
    kwargs...
)
```

`LogDensityModel` と MCMC チェーン（事後または事前からサンプリングされた）を使用して、軌道を視覚化する 9 枚のプロットのパネルを生成します。出力はシステムの名前に基づいてファイルに保存されます（`fname`）。
