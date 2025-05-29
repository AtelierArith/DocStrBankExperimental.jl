function troendle(perm::AbstractMatrix,stat::AbstractVector;type=:twosided)

Troendle 1995 における多重比較補正

`perm` のサイズは ntests x nperms

`stat` のサイズは ntests

`type` は :twosided (デフォルト)、:lesser、:greater のいずれかです

Jaromil Frossard による permuco の R 実装に強く影響を受けています

注意: permuco は BSD の下でリリースされていますが、著者の Jaromil Frossard は troendle および clusterdepth R 関数に対して MIT ライセンスを提供してくれました。
