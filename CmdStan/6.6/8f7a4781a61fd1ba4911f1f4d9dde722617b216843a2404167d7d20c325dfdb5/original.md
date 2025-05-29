# extract(chns::Array{Float64,3}, cnames::Vector{String})

RStan/PyStan style extract chns: Array: [draws, vars, chains], cnames: ["lp**", "accept_stat**", "f.1", ...] Output: name -> [size..., draws, chains]
