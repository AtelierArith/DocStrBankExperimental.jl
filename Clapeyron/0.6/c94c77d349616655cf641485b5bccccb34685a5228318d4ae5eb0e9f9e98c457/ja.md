```
gibbs_solvation(model::EoSModel, T; threaded=true, vol0=(nothing,nothing))
```

溶媒自由エネルギーを次のように計算します：

```julia
g_solv = -R̄*T*log(K)
```

ここで、最初の成分は溶媒で、2番目は溶質です。
