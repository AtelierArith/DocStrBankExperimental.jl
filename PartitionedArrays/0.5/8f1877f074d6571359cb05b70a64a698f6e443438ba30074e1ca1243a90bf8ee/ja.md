```
map_main(f,args...;kwargs...)
```

`map(f,args...)`のようですが、`args`の配列の1つのコンポーネントにのみ`f`を適用します。

# オプションのキーワード引数

  * `main = MAIN`: マッピングするコンポーネントの線形インデックス
  * `otherwise = (args...)->nothing`: `main`とは異なるインデックスをマッピングする際に適用する関数。

# 例

```jldoctest
julia> using PartitionedArrays

julia> a = [1,2,3,4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> map_main(-,a,main=2)
4-element Vector{Union{Nothing, Int64}}:
   nothing
 -2
   nothing
   nothing
```
