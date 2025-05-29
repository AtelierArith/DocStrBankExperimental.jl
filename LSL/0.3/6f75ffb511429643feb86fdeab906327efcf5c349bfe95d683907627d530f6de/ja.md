push_chunk(outlet::StreamOutlet{T},            data::Matrix{T};            timestamp = 0.0,            pushthrough = true)

アウトレットにサンプルのチャンクをプッシュします。

各サンプルは、行列 `data` の列で構成されており、サイズは size(data) = (M,N) で、ここで M はアウトレットのチャネル数、N はチャンク内のサンプル数です。

# キーワード引数

-`timestamp::Number`: サンプルのキャプチャ時間で、`local_clock()` と一致します。省略された場合、現在の時間が使用されます。

  * `passthrough::Bool`: サンプルを受信者にプッシュするか、後続のサンプルとバッファリングするかを指定します。チャンクサイズがアウトレットの構築時に指定されている場合、pushthrough フラグよりも優先されます。
