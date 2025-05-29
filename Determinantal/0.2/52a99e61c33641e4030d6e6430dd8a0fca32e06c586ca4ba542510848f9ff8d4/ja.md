```
kl_divergence(L1::AbstractLEnsemble,L2::AbstractLEnsemble,k::Int;nsamples=100)
```

2つの(k-)DPP間のKLダイバージェンスを推定します。KLダイバージェンスは、L-アンサンブルL1を持つk-DPPからサンプリングし、確率の平均対数比を計算することで推定されます。nsamplesは、どれだけのサンプルが取られるかを制御します。
