# extract(chns::Array{Float64,3}, cnames::Vector{String})

RStan/PyStanスタイルのextract chns: Array: [draws, vars, chains], cnames: ["lp**", "accept_stat**", "f.1", ...] 出力: name -> [size..., draws, chains]
