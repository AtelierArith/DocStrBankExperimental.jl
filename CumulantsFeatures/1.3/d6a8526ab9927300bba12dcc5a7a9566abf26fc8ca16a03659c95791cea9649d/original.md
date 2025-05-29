function hosvdc4detect(X::Matrix{T}, β::Float64 = 4.1, r::Int = 3; b::Int = 4)

Takes data in the form of matrix where first index correspond to realisations and second to feratures (marginals). Using the HOSVD of the 4'th cumulant's tensor of data returns the array of Bool that correspond to outlier realisations. β is the sensitivity parameter while r a number of specific directions, data are projected onto. Parameter b is a size of blocks in a SymmetricTensors structure

```jldoctest
julia> Random.seed!(42);

julia> x = vcat(rand(8,2), 20*rand(2,2))
10×2 Array{Float64,2}:
  0.533183    0.956916
  0.454029    0.584284
  0.0176868   0.937466
  0.172933    0.160006
  0.958926    0.422956
  0.973566    0.602298
  0.30387     0.363458
  0.176909    0.383491
 11.8582      5.25618
 14.9036     10.059

julia> rxdetect(x, 0.95)
10-element Array{Bool,1}:
 false
 false
 false
 false
 false
 false
 false
 false
  true
  true
```
