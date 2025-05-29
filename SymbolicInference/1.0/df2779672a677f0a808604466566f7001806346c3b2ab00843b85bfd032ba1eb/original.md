extract*recurrences(data*source::Vector{Float64}, motifs*dict::Dict{String, Vector}; num*windows::Int64 = 3)

This function returns x and y coordinates for a given window considering start and size of each motif. The y coordinates are the values from data provided by the user. 
