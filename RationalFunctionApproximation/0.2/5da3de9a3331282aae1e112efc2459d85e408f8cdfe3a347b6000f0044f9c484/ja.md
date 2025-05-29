```
rewind(r, index)
```

反復中に遭遇した状態に対して有理近似を巻き戻します。

# 引数

  * `r::Approximation}`: 巻き戻す近似
  * `index::Integer`: 巻き戻す反復番号

# 戻り値

  * 指定されたインデックスの有理関数（入力と同じ型）

# 例

```jldoctest
julia> r = approximate(x -> cos(20x), unit_interval)
Barycentric{Float64, Float64} 有理補間子の型 (24, 24) のドメイン: Path{Float64} で 1 つの曲線

julia> rewind(r, 10)
Barycentric{Float64, Float64} 有理補間子の型 (10, 10) のドメイン: Path{Float64} で 1 つの曲線
```
