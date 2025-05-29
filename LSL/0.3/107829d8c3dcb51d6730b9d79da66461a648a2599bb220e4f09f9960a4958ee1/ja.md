```
push_sample(outlet::StreamOutlet{T},
            data::Vector{T};
            timestamp = 0.0,
            pushthrough = true)
```

アウトレットにサンプルをプッシュします。ベクター内の各エントリは1つのチャネルに対応します。

# キーワード引数

  * `timestamp::Number`: サンプルのキャプチャ時間。`local_clock()`と一致し、指定しない場合は現在の時間が使用されます。

      * `passthrough::Bool`: サンプルを受信者にプッシュするか、後続のサンプルとバッファリングするかを指定します。アウトレットの構築時に指定されたchunk_sizeは、pushthroughフラグよりも優先されます。
