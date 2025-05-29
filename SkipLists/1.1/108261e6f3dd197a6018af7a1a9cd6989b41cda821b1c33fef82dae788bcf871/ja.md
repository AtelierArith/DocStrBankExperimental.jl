```
SkipList{T,M} <: AbstractSkipList{T,M}
```

非同時スキップリストです。`T`は`SkipList`に格納できる要素の型で、`M`はリストのモードです：

  * `M == :List`：同じキーをスキップリストに複数回格納できます。
  * `M == :Set`：スキップリストには各キーのコピーは1つだけ許可されます。`SkipListSet{T}`は`SkipList{T,:Set}`のエイリアスです。

# 例

```jldoctest; setup = :(using SkipLists)
julia> list = SkipList{Int64}();

julia> insert!(list, 1); insert!(list, 2); insert!(list, 3);

julia> collect(list)
3-element Vector{Int64}:
 1
 2
 3
```
