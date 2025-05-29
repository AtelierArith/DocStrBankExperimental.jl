`node_type` 関数を使用して、近似層 `mu` と `domain` を持つ `d` 次元の完全 Smolyak グリッドを構築します。`domain` が提供されていない場合、近似ドメインはデフォルトで [1.0,-1.0]^d になります。完全 Smolyak グリッドと関連するマルチインデックスを返します。

# シグネチャ

full*grid, mi = smolyak*grid*full(chebyshev*extrema,d,mu,domain)

# 例

```
julia> full_grid, mi = smolyak_grid_full(chebyshev_extrema,2,2)
julia> full_grid, mi = smolyak_grid_full(chebyshev_extrema,2,[2,1])
julia> full_grid, mi = smolyak_grid_full(chebyshev_extrema,2,2,[3.0 1.5; 2.0 0.5])
julia> full_grid, mi = smolyak_grid_full(chebyshev_extrema,2,[2,2],[3.0 1.5; 2.0 0.5])
```
