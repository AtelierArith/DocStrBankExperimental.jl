チェビシェフ多項式を基底関数として使用し、近似グリッド `grid`、`multi_index`、および近似 `domain`（デフォルトは [1.0,-1.0]^d）に対してスモリャク多項式近似の逆補間行列を計算します。逆補間行列を含む行列を返します。

# シグネチャ

iim = smolyak*inverse*interpolation*matrix(grid,multi*index,domain)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> iim = smolyak_inverse_interpolation_matrix(g,mi)
```
