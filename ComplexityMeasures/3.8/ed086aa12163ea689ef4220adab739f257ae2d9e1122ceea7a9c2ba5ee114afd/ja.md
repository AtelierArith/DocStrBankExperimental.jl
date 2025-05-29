```
FluctuationComplexity <: InformationMeasure
FluctuationComplexity(; definition = Shannon(; base = 2), base = 2)
```

「フラクチュエーション複雑性」は、PMFの要約統計量（[`InformationMeasure`](@ref)）の周りの状態 $\omega_i$ の情報量の標準偏差を定量化します。具体的には、結果空間 $\Omega$ における結果 $\omega_i \in \Omega$ と確率質量関数 $p(\Omega) = \{ p(\omega_i) \}_{i=1}^N$ が与えられたとき、次のように定義されます。

$$
\sigma_I(p) := \sqrt{\sum_{i=1}^N p_i(I_i - H_*)^2}
$$

ここで、$I_i = -\log_{base}(p_i)$ は i 番目の結果の情報量です。情報量のタイプ $*$ は `definition` によって制御されます。

`base` は情報量の項に入る対数の底を制御します。`definition` に選ばれた底と一貫性のある `base` を選択してください（例えば、[`Shannon`](@ref) に関連します）。

## 特性

`definition` が [`Shannon`](@ref) エントロピーである場合、[Bates1993](@cite) から [Shannon 型情報フラクチュエーション複雑性](https://en.wikipedia.org/wiki/Information_fluctuation_complexity) を回復します。この場合、フラクチュエーション複雑性は、非ゼロ要素が1つだけのPMFや、均一分布の場合にはゼロになります。

`definition` がシャノンエントロピーでない場合、測定の特性は異なり、必ずしも [Bates1993](@cite) の特性を共有するわけではありません。

!!! note "新しい研究の可能性"
    我々の知る限り、フラクチュエーション複雑性に対してシャノンエントロピー以外の他の情報量を使用することは、文献ではまだ探求されていません。しかし、我々の実装ではそれが可能です。新しい組み合わせを試した場合は、ぜひお知らせください！

