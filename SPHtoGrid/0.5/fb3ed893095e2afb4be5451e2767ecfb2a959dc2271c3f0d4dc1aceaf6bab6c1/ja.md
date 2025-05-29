```
distributed_allsky_map( allsky_filename::String, 
                        Nside::Integer, Nsubfiles::Integer, 
                        mapping_function::Function;
                        reduce_image::Bool=true)
```

サブファイルごとに1つの全空間マップを計算するためにワーカーを動的にディスパッチし、結果を合計してfitsファイルに保存します。

# 引数

  * `allsky_filename::String`: 画像を保存するファイルの名前
  * `Nside::Integer`: healpixマップのための`Nside`、2の累乗でなければなりません！ `Nside = 2^N`。
  * `Nsubfiles::Integer`: スナップショットが分散されるサブファイルの数。
  * `mapping_function::Function`: サブファイルごとに実行される関数。戻り値として[`allsky_map`](@ref)への呼び出しを持っている必要があります。
  * `reduce_image`: 最終画像が重み画像で割られるべきかどうか、`true`に設定します。
