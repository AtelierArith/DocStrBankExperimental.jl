```
jackknife(
    g::Function,
    samples...;
    # キーワード引数
    bias_corrected = true,
    jackknife_samples = similar.(samples),
    jackknife_g = similar(samples[1])
)
```

関数 `g` の評価を通じてエラーを伝播させ、ビンに分けられた `samples` に基づいて平均とエラーの両方を返します。キーワード引数 `bias = true` の場合、$\mathcal{O}(1/N)$ バイアスが修正されます。キーワード引数 `jackknife_samples` と `jackknife_g` を渡すことで、一時的なメモリ割り当てを避けることができます。
