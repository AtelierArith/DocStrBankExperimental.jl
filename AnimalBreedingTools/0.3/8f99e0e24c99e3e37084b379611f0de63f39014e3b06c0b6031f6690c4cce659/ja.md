```
vare = hrv_class(ve,rangeset)
```

異質な残差分散のベクトル `ve` と範囲のセット `rangeset` から残差分散を含むベクトルを生成します。

```juliadoctests
julia> vare = hrv_class([10.0,20.0],[3:5,6:9])
7-element Vector{Float64}:
10.0
10.0
10.0
20.0
20.0
20.0
20.0
```
