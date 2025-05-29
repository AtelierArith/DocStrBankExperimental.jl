```julia
draw_from_distribution(dist::Collection{AbstractFloat}, n::Integer)
```

コレクション `dist` によって指定された連続確率分布から `n` 個のランダム浮動小数点数を引き出します。このコレクションは、そのPDF曲線を定義します。

### 例

```julia
julia> draw_from_distribution([0,1,2,1,0.], 7)
7-element Vector{Float64}:
 0.5271744125470383
 0.6624591724796276
 0.7737643383545575
 0.9603780726501608
 0.7772477857811155
 0.8307248435614027
 0.6351766227803024    
```
