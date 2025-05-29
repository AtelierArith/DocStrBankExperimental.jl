```
TaylorParam(k::Int, t::L, H::Matrix, x::Array{CPType,1})

TaylorParam(k::Int,t::L,prob::QuLDEProblem{uType, tType, isinplace, F, P, T})
```

テイラー級数に基づくハミルトニアンシミュレーションに必要なパラメータに値を割り当てます。

```
* k : テイラー級数展開の次数を設定
* t : 発展の時間
* H : ハミルトニアン
* x : 初期ベクトル
* prob : 線形微分方程式問題のラッパー（H、x、bを含む）
```
