```julia
add*allcyclones!(addition :: Array{T,2}, buf :: Array{T,2}, array :: Array{T,2}, radius*bins, array :: Array{T,3}, segmentedcyclones, cyclonescenters, gridspacing)

中心の周りの量の方位平均を計算します。プロセスを繰り返し、配列上で検出されたすべての熱帯サイクロンについて平均化します。使用する半径ビンを持つ配列、平均化するフィールド（`array`と呼ばれる）、各サイクロンをセグメント化された画像として、サイクロンの中心、およびグリッド間隔を受け取ります。
```
