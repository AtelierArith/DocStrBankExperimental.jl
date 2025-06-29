```
sir(
    β = 0.5, γ = 0.25, N = 10000,
    ρ = 0.3, k = 10,
    S₀ = 0.9, I₀ = 0.01, R₀ = 0.1,
    δt = 0.1, t₀ = 0.0,
    times = range(start=1.0,stop=90,step=1.0)
   )
```

`sir` はシミュレーションされた SIR データを含む *PompObject* を返します。

## パラメータ

  * β: 伝播率
  * γ: 回復率
  * N: 人口サイズ
  * ρ: 報告率
  * k: 過分散係数（負の二項分布のサイズパラメータ）
  * S₀, I₀, R₀: t=t₀ における人口の感受性、感染、回復の相対的割合（それぞれ）
  * δt: オイラーのステップサイズ
  * t₀: ゼロ時間
  * times: 観測時間のベクトル
