```
intensity_trace(f::GenericFluor, nframes::Int, framerate::Real; state1=1)
```

蛍光状態の占有中に放出を統合することによって蛍光強度トレースを計算します。

# 引数

  * `f::GenericFluor`: 遷移率 (q) と放出率 (γ) を含む蛍光体モデル
  * `nframes::Int`: シミュレーションするフレーム数
  * `framerate::Real`: フレームレート (Hz)
  * `state1::Int=1`: 初期状態 (デフォルト: 蛍光状態のため1)

# 戻り値

  * `Vector{Float64}`: 各フレームの統合された光子カウント

# 詳細

各フレームについて:

1. CTMCを使用して状態の占有を決定します
2. 蛍光状態の期間中に放出 (率 f.γ) を統合します
3. フレーム露出時間内に光子を蓄積します (1/framerate)

# 例

```julia
fluor = GenericFluor(; γ=10000.0, q=[-10.0 10.0; 1e-1 -1e-1])
photons = intensity_trace(fluor, 1000, 10.0)
```

# 注意

  * 状態1は蛍光状態であると仮定されます
  * 放出は状態1でのみ率 f.γ で発生します
  * フレーム露出は 1/framerate (100% デューティサイクル) であると仮定されます
