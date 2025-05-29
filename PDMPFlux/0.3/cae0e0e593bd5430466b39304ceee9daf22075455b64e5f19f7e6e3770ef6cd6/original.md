スケルトンからサンプリングをし，各行ベクトルに次元毎の時系列が格納された Matrix{Float64} を返す．

Args:     N (Int): The number of samples to generate.     output (PdmpOutput): The PDMP output containing the trajectory information.

Returns:     Array{Float64, 2}: The sampled points from the PDMP trajectory skeleton.
