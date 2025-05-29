```
fit_spectrum(
    hs::Spectrum|HyperSpectrum,
    vq::VectorQuant{S <: Detector, T <: AbstractFloat},
    zero = x -> max(Base.zero(T), x)
)
```

スペクトルまたはハイパースペクトルをベクトル量子化アルゴリズムを使用してフィットします。関数 `zero` は、結果の k 比率に適用され、返される前に処理されます。デフォルトでは、負の k 比率を 0.0 に設定します。 `zero=identity` は、負の k 比率をそのままにします。
