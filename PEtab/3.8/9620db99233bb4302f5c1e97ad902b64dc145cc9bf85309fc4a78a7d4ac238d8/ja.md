```
get_obs_comparison_plots(res, prob::PEtabODEProblem; kwargs...)::Dict
```

すべてのシミュレーション条件とすべての可観測IDに対して、PEtab.jlパラメータ推定結果（`res`）のデータに対するモデルフィットをプロットします。

返される`Dict`の各エントリは、すべての可能な`cid`とすべての`obsid`に対して`plot(res, prob; obsids=[obsid], cid=cid, kwargs...)`に対応しています。
