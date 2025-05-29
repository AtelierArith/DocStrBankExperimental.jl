ベクトルのリストに対して特徴行列を作成します。結果の行列では、各列 c はパラメータベクトルに対する SCS との整合性を表し、各行 r は1つの特徴を表し、各セルの値 r,c はベクトル c における特徴 r の値です。

# 例

```jldoctest
julia> featurematrix([1,3,5], [4,5,6])
5×2 Matrix{Any}:
	1          nothing
	3          nothing
	nothing  4
	5         5
	nothing  6	
```

```julia
featurematrix(v; norm, cf)

```
