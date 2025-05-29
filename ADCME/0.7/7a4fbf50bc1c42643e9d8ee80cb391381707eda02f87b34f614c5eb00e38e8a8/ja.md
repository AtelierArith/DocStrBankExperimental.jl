```
dtw(s::Union{PyObject, Array{Float64}}, t::Union{PyObject, Array{Float64}}, 
    use_fast::Bool = false)
```

2つの時系列 `s` と `t` の間の動的時間ワープ（DTW）距離を計算します。 距離とパスを返します。 `use_fast` は、高速アルゴリズムが使用されるかどうかを指定します。 注意：高速アルゴリズムは正確でない場合があります。
