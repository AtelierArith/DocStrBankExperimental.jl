```
TDE(datacube::Array{tp, 4}, ΔT::Integer, DIM::Int = 3) where {tp}
TDE(datacube::Array{tp, 3}, ΔT::Integer, DIM::Int = 3) where {tp}
```

は、遅延バージョンの2次元、3次元、または4次元のデータキューブを、次元 `DIM` までの過去 `ΔT` タイムステップで連結することによって、埋め込まれたデータキューブを返します（プリセット: `DIM = 3`）

# 例

```
julia> dc = randn(50,3)
julia> TDE(dc, 3, 2)
```
