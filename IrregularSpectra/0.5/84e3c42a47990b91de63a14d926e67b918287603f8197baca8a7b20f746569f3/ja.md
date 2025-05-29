`Prolate1D(bandwidth::Float64, intervals::Vector{NTuple{2,Float64}}, ntaper::Int64)`

`intervals`上でサポートされ、半帯域幅`bandwidth`を持つ（一般化された）プロレート関数。カイザーのような閉形式のウィンドウとは異なり、この関数とそのフーリエ変換は、数値的に積分固有値問題を解くことによってのみ利用可能です。このため、スカラー評価メソッド`(p::Prolate1D)(x)`や`IrregularSpectra.fouriertransform(p::Prolate1D, ω::Float64)`は意図的に実装されていません。

`Prolate1D`には次の構築メソッドがあります。

`Prolate1D(intervals;             bandwidth=default_bandwidth(intervals),            ntaper=default_ntaper(intervals, bandwidth))`

これは、自動的に帯域幅とテーパーの数（1より大きい可能性があります）を選択します。`ntapers>1`の場合、得られる推定量はマルチテーパー推定量になります。
