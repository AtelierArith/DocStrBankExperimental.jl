```
fit(DMRPaths,covars,counts; <keyword arguments>)
dmrpaths(covars,counts; <keyword arguments>)
```

カウントに対する分散多項式回帰（DMR）をフィットし、全体の正則化パスを返します。これは、プロットやAICc最適以外の係数を選択するのに役立つ場合があります。引数は[`fit(::DMR)`](@ref)と同じです。
