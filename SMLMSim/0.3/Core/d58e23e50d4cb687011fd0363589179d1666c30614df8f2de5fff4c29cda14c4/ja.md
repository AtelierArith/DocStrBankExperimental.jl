```
CTMC(q::Array{T}, simulation_time::T, state1::Int) where {T<:AbstractFloat}
```

レート行列から連続時間マルコフ連鎖シミュレーションを構築します。

# 引数

  * `q::Array{T}`: レート行列で、q[i,j]（i≠j）は状態iからjへの遷移レート、q[i,i]は状態iからの負の退出レートです
  * `simulation_time::T`: シミュレーションする総時間
  * `state1::Int`: 初期状態

# 戻り値

  * `CTMC{T,Int}`: 遷移時間と状態を持つシミュレートされたCTMC

# 詳細

ギレスピーアルゴリズムを使用してCTMCをシミュレートします：

1. 時間0でstate1から開始
2. 現在の状態iについて：

      * 総退出レートk*tot = Σ*j q[i,j]を計算
      * 次の遷移までの時間をExp(k_tot)からサンプリング
      * 確率q[i,j]/k_totで次の状態jをサンプリング
3. simulation_timeを超えるまで繰り返す

```
