```
fit(HDMRPaths,covars,counts; <keyword arguments>)
hdmrpaths(covars,counts; <keyword arguments>)
```

カウントに対する障害分布多項式回帰 (HDMR) を covars にフィットさせ、プロットや AICc 最適以外の係数を選択するのに役立つ可能性のある全体の正則化パスを返します。引数は [`fit(::HDMR)`](@ref) と同じです。
