```
missingsmallest(x, y)
```

標準部分順序 `isless` は、`missing` が常に最小の値になるように修正されています：

  * どちらの引数も `missing` でない場合、関数は `isless` と全く同じように動作します。
  * `y` が `missing` の場合、結果は `x` の値に関わらず `false` になります。
  * `x` が `missing` の場合、結果は `y` が `missing` でない限り `true` になります。

上記のように `missing` を扱う部分順序関数（例えば `isless`）を受け取る1引数メソッドも参照してください。これらの関数は、欠損値が最初にソートされるようにソート関数と一緒に使用できます。これは特に、逆順でソートする際に欠損値が最後に表示されるようにするために便利です。

# 例

```jldoctest julia> sort(v, lt=missingsmallest) 5-element Vector{Union{Missing, Int64}}:    missing    missing   1   2  10

julia> sort(v, lt=missingsmallest, rev=true) 5-element Vector{Union{Missing, Int64}}:  10   2   1    missing    missing

julia> missingsmallest(missing, Inf) true

julia> missingsmallest(-Inf, missing) false

julia> missingsmallest(missing, missing) false
```
