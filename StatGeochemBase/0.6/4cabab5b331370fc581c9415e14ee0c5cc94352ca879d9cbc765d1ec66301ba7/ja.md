```julia
n = count_unique!(A)
```

配列 `A` をインプレースでソートし（すでにソートされていない場合）、ユニークな要素を前方に移動し、見つかったユニークな要素の数を返します。

`A[1:count_unique!(A)]` は `unique(A)` と同等の配列を返すべきです。

### 例

```julia
julia> A = rand(1:5, 10)
10-element Vector{Int64}:
 4
 4
 2
 3
 3
 4
 1
 5
 1
 2

julia> A = rand(1:5, 7)
7-element Vector{Int64}:
 1
 1
 4
 3
 1
 1
 4

julia> n = count_unique!(A)
3

julia> A
7-element Vector{Int64}:
 1
 3
 4
 1
 3
 4
 4

julia> A[1:n]
3-element Vector{Int64}:
 1
 3
 4
```
