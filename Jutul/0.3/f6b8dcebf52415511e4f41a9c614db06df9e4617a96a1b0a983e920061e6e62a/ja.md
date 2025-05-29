```
allocate_array_ad(n[, m]; <keyword arguments>)
```

ADとしてベクトルまたは行列を割り当て、オプションで提供されたコンテキストと指定された非ゼロの対角線を持ちます。

# 引数

  * `n::Integer`: ベクトルのエントリ数、または `m` が指定されている場合の行数。
  * `m::Integer`: 行数（オプション）

# キーワード引数

  * `npartials = 1`: 各要素に割り当てる部分導関数の数
  * `diag_pos = nothing`: 対角線上にエンティティを配置するインデックス（ある場合）

他のキーワード引数は `get_ad_entity_scalar` に渡されます。

# 例:

単一の部分でベクトルを割り当てます：

```julia-repl
julia> allocate_array_ad(2)
2-element Vector{ForwardDiff.Dual{nothing, Float64, 1}}:
 Dual{nothing}(0.0,0.0)
 Dual{nothing}(0.0,0.0)
```

二つの部分でベクトルを割り当て、最初の部分を1に設定します：

```julia-repl
julia> allocate_array_ad(2, diag_pos = 1, npartials = 2)
2-element Vector{ForwardDiff.Dual{nothing, Float64, 2}}:
 Dual{nothing}(0.0,1.0,0.0)
 Dual{nothing}(0.0,1.0,0.0)
```

二つの部分を持つ行列を設定し、最初の列に部分 [1, 0]、二番目に [0, 1] を持たせます：

```julia-repl
julia> allocate_array_ad(2, 2, diag_pos = [1, 2], npartials = 2)
2×2 Matrix{ForwardDiff.Dual{nothing, Float64, 2}}:
 Dual{nothing}(0.0,1.0,0.0)  Dual{nothing}(0.0,1.0,0.0)
 Dual{nothing}(0.0,0.0,1.0)  Dual{nothing}(0.0,0.0,1.0)
```
