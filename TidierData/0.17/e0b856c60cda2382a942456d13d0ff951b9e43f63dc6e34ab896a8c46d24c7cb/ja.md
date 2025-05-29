```
ntile(x, n::Integer)
```

入力ベクトルを `n` 個の同じサイズのバケットに分割します。

`ntile()` は、入力ベクトルを `n` 個のバケットに分割する粗いランクです。`length(x)` が `n` の整数倍でない場合、バケットのサイズは最大で1の差があり、大きいバケットが先に来ます。

他のランク付け関数とは異なり、`ntile()` はタイを無視します：同じ値の `x` が異なるバケットに入っても、均等なサイズのバケットを作成します。

# 引数

  * `x`: ランク付けするベクトル。デフォルトでは、最小の値が最小のランクを得ます。欠損値にはランク `missing` が与えられます。
  * `n`: バケットに分けるグループの数。

# 例

```jldoctest
julia> x = [5,1,3,2,2, missing]
6-element Vector{Union{Missing, Int64}}:
 5
 1
 3
 2
 2
  missing

julia> ntile(x, 2)
6-element Vector{Union{Missing, Int64}}:
 2
 1
 2
 1
 1
  missing

julia> ntile(x, 4)
6-element Vector{Union{Missing, Int64}}:
 4
 1
 3
 1
 2
  missing

julia> ntile(1:8, 3)
8-element Vector{Int64}:
 1
 1
 1
 2
 2
 2
 3
 3

julia> df = DataFrame(a = 1:8);

julia> @chain df begin
       @mutate(buckets = ntile(a, 3))
       end
8×2 DataFrame
 Row │ a      buckets 
     │ Int64  Int64   
─────┼────────────────
   1 │     1        1
   2 │     2        1
   3 │     3        1
   4 │     4        2
   5 │     5        2
   6 │     6        2
   7 │     7        3
   8 │     8        3
```
