メソッド1は関数内で摂動を生成し、辞書チェーンを作成して返し、最終モデルの推定値をその場で修正します。このメソッドは、フィッティングの品質、チェーン診断、モデルのサンプラーの最適化など、いくつかのボクセルをチェックするのに便利です。

```
mcmc!(
    estimates::BiophysicalModel,
    meas::Vector{Float64},
    protocol::Protocol,
    sampler::Sampler,
    noise::Noisemodel = Noisemodel(),
    rng::Int64 = 1
)
```

```julia-repl
julia> chain = mcmc!(estimates, measurements, protocol, sampler, noise_model, rng)
```

メソッド2は`chain`と`pertubations`を入力として受け取り、`chain`をその場で変更し、最終的な推定値と不確実性を計算するために使用されます。このメソッドは、全脳/スライスなどの大規模データセットを処理するために使用されます。このメソッドは、チェーンのキャッシングのためにスペースを事前に割り当て、各ボクセルのためにそれらを作成するのを避けるマルチスレッド処理と一緒に使用されます。このメソッドは、より高速な計算速度のために`pertubations`を再利用します。通常、非常に大きな数の摂動（例：~10^4）を使用して提案分布を密にサンプリングします。

```
mcmc!(
    chain::Vector{Any},
    estimates::BiophysicalModel,
    meas::Vector{Float64},
    protocol::Protocol,
    sampler::Sampler,
    pertubations::Vector{Vector{Any}},
    noise::Noisemodel = Noisemodel()
)
```

```julia-repl
julia> mcmc!(chain, estimates, meas, protocol, sampler, pertubations, noise_model))
```

# 参考文献

マイクロストラクチャーイメージングにおけるMCMCの使用について、以下の推奨参考文献があります：

Behrens, T.E.J., Woolrich, M.W., Jenkinson, M., Johansen-Berg, H., Nunes, R.G., Clare, S., Matthews, P.M., Brady, J.M., Smith, S.M., 2003. Characterization and Propagation of Uncertainty in Diffusion-Weighted MR Imaging. Magn Reson Med 50, 1077–1088. https://doi.org/10.1002/MRM.10609

Alexander, D.C., 2008. A General Framework for Experiment Design in Diffusion MRI and Its Application in Measuring Direct Tissue-Microstructure Features. Magn Reson Med 60, 439–448. https://doi.org/10.1002/mrm.21646
