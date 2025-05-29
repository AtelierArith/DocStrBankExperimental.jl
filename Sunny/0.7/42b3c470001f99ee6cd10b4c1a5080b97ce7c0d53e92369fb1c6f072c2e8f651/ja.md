```
minimize_energy!(sys::System{N}; maxiters=1000, method=Optim.ConjugateGradient(),
                 kwargs...) where N
```

`sys`内のスピン配置を最適化してエネルギーを最小化します。合計で`maxiters`回の反復が試みられます。`method`パラメータは、[Optim.jlパッケージ](https://github.com/JuliaNLSolvers/Optim.jl)の`optimize`関数で使用されます。残りの`kwargs`は、Optim.jlの`Options`コンストラクタに含まれます。
