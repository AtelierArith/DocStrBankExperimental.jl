スケルトンからサンプリングをし，各行ベクトルに次元毎の時系列が格納された Matrix{Float64} を返す．

Args:     N (Int): 生成するサンプルの数。     output (PdmpOutput): 軌道情報を含む PDMP 出力。

Returns:     Array{Float64, 2}: PDMP 軌道スケルトンからのサンプル点。
