```jldoctest
julia> using GroundMotion

julia> array = rand(Float64, 3, 4)  # 2D array of Float64

julia> point_vs30_array = Array{GroundMotion.Point_vs30, 1}(undef, size(array, 1))

julia> for i in 1:size(array, 1)
           point_vs30_array[i] = GroundMotion.Point_vs30(array[i, :])
       end
```
