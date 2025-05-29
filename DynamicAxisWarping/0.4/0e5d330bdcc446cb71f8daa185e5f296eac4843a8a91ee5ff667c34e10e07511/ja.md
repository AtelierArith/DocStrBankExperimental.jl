```
cost,i1,i2 = fastdtw(seq1,seq2,dist,radius)
```

FastDTWアルゴリズムを使用して、2つのシーケンス間の距離を測定する動的時間ワーピングを実行します。通常、通常のDTWはFastDTWよりも優れたパフォーマンスを発揮することに注意してください https://arxiv.org/abs/2003.11246

Salvador & Chanによって説明されたDTWのFastDTW近似を計算します。Intelligent Data Analysis (2007)。

他にも[`dtw`](@ref)、[`dtw_cost`](@ref)、[`dtwnn`](@ref)を参照してください。
