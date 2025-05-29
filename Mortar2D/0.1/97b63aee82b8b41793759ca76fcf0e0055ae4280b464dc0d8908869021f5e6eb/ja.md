```
calculate_mortar_assembly(elements::Dict{Int, Vector{Int}},
                          element_types::Dict{Int, Symbol},
                          coords::Dict{Int, Vector{Float64}},
                          slave_element_ids::Vector{Int},
                          master_element_ids::Vector{Int})
```

与えられたデータに基づいて、射影行列 `D` と `M` を計算します。これはパッケージのメイン関数です。行列の関係は $D u_s = M u_m$ であり、ここで $u_s$ はスレーブノード、$u_m$ はマスターノードです。

# 例

README.md の単純な問題のためにモルターマトリックスを計算します。

```jldoctest ex1
Xs = Dict(1 => [0.0, 1.0], 2 => [5/4, 1.0], 3 => [2.0, 1.0])
Xm = Dict(4 => [0.0, 1.0], 5 => [1.0, 1.0], 6 => [2.0, 1.0])
coords = merge(Xm , Xs)
Es = Dict(1 => [1, 2], 2 => [2, 3])
Em = Dict(3 => [4, 5], 4 => [5, 6])
elements = merge(Es, Em)
element_types = Dict(1 => :Seg2, 2 => :Seg2, 3 => :Seg2, 4 => :Seg2)
slave_element_ids = [1, 2]
master_element_ids = [3, 4]
s, m, D, M = calculate_mortar_assembly(elements, element_types, coords,
                                       slave_element_ids, master_element_ids)

# 出力

([1, 2, 3], [4, 5, 6],
  [1, 1]  =  0.416667
  [2, 1]  =  0.208333
  [1, 2]  =  0.208333
  [2, 2]  =  0.666667
  [3, 2]  =  0.125
  [2, 3]  =  0.125
  [3, 3]  =  0.25,
  [1, 4]  =  0.366667
  [2, 4]  =  0.133333
  [1, 5]  =  0.25625
  [2, 5]  =  0.65
  [3, 5]  =  0.09375
  [1, 6]  =  0.00208333
  [2, 6]  =  0.216667
  [3, 6]  =  0.28125)

```

`s` と `m` にはスレーブおよびマスターの自由度が含まれています：

```jldoctest ex1
julia> s, m
([1, 2, 3], [4, 5, 6])
```

`D` はスレーブ側のモルターマトリックスです：

```jldoctest ex1
julia> full(D[s,s])
3×3 Array{Float64,2}:
 0.416667  0.208333  0.0
 0.208333  0.666667  0.125
 0.0       0.125     0.25
```

`M` はマスター側のモルターマトリックスです：

```jldoctest ex1
julia> full(M[s,m])
3×3 Array{Float64,2}:
 0.366667  0.25625  0.00208333
 0.133333  0.65     0.216667
 0.0       0.09375  0.28125
```
