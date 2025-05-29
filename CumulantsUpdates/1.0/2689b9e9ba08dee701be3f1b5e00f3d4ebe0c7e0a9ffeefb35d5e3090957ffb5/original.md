function cumulantsupdate!(dm::DataMoments{T}, Xplus::Matrix{T}) where T <: AbstractFloat

updates the DataMoments structure in a sliding window, given an updat Xplus and returns cumululants of updated data.

```jldocstests

julia> x = ones(10,2);

julia> s = DataMoments(x, 4, 2);

julia> y = zeros(4,2);

julia> cumulantsupdate!(s,y)[4]
SymmetricTensors{Float64,4}(Union{Array{Float64,4}, Void}[[0.0064 0.0064; 0.0064 0.0064]

[0.0064 0.0064; 0.0064 0.0064]

[0.0064 0.0064; 0.0064 0.0064]

[0.0064 0.0064; 0.0064 0.0064]], 2, 1, 2, true)

```
