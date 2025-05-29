```
mutable struct KPMExpansion{T<:AbstractFloat, Tfft<:FFTW.r2rFFTWPlan}
```

KPMアルゴリズムで使用されるチェビシェフ多項式展開を表す型です。

# フィールド

  * `M::Int`: チェビシェフ多項式展開の次数。
  * `bounds::NTuple{2,T}`: KPMアルゴリズムにおける固有スペクトルの範囲。
  * `buf::Vector{T}`: このベクトルの最初の `M` 要素はチェビシェフ展開係数です。
  * `r2rplan::Tfft`: チェビシェフ-ガウス数値積分を介してチェビシェフ展開係数を効率的に計算するためのDCTを実行するための計画。
