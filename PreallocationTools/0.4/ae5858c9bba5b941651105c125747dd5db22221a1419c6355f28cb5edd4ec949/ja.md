`FixedSizeDiffCache(u::AbstractArray, N = Val{default_cache_size(length(u))})`

`u`のキャッシュのバージョンと`u`の`Dual`バージョンの両方を保存する`FixedSizeDiffCache`オブジェクトを構築し、順方向自動微分を使用して事前キャッシュされたベクトルを利用できるようにします。
