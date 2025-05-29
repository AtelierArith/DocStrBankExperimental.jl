```
IpoptOptimizer(LBFGS::Bool)
```

パラメータ推定のために[Ipopt](https://coin-or.github.io/Ipopt/)内部点ニュートン法オプティマイザを設定します。

Ipoptは、`PEtabODEProblem`からのヘッセ行列法（`LBFGS=false`）またはLBFGSスキーム（`LBFGS=true`）のいずれかを使用するように構成できます。他のIpoptオプションの設定については、[`IpoptOptions`](@ref)を参照してください。

また、[`calibrate`](@ref)および[`calibrate_multistart`](@ref)も参照してください。

## 説明

Ipoptは、制約付き非線形最適化問題のための内部点ニュートン法です。アルゴリズムに関する詳細情報は[1]にあります。

1. Wächter and Biegler, Mathematical programming, pp 25-57 (2006)
