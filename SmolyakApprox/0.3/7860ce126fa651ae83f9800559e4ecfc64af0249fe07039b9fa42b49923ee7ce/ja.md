チェビシェフ多項式を基底関数として使用し、近似グリッド `grid`、`multi_index`、および近似 `domain`（デフォルトは [1.0,-1.0]^d）を考慮して、スモリャク多項式近似の逆補間行列をマルチスレッドで計算します。逆補間行列を含む行列を返します。

# シグネチャ

iim = smolyak*inverse*interpolation*matrix*threaded(grid,multi_index,domain)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> iim = smolyak_inverse_interpolation_matrix_threaded(g,mi)
```
