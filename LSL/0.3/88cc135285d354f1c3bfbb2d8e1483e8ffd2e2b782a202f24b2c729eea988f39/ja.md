push_chunk(outlet::StreamOutlet{T},            data::Matrix{T},            timestamp::Vector{Float64};            pushthrough = true)

個々のタイムスタンプを持つサンプルのチャンクをアウトレットにプッシュします。

各サンプルは、行列 `data` の列で構成されており、サイズは `size(data) = (M,N)` で、ここで M はアウトレットのチャネル数、N はチャンク内のサンプル数です。

# 引数

  * `timestamps`: サンプルのキャプチャ時間で、`local_clock()` と一致します。省略された場合は、現在の時間が使用されます。

# キーワード引数

  * `passthrough::Bool`: サンプルを受信者にプッシュするか、後続のサンプルとバッファリングするかを指定します。チャンクサイズがアウトレットの構築時に指定されている場合は、`pushthrough` フラグよりも優先されます。
