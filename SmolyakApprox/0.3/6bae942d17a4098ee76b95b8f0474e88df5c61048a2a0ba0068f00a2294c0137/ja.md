`node_type` 関数を使用して、近似層 `mu` と `domain` を持つ `d` 次元 Smolyak グリッドを構築します。 `mu` が整数（整数のベクトル）の場合、等方性（非等方性）グリッドが構築されます。近似グリッドと関連する多重インデックスを返します。 `domain` が提供されていない場合、近似ドメインはデフォルトで [1.0,-1.0]^d になります。

# シグネチャ

grid, multi*index = smolyak*grid(node*type,d,mu) grid, multi*index = smolyak*grid(chebyshev*extrema,d,mu,domain)

# 例

```
julia> grid, m_index = smolyak_grid(chebyshev_extrema,2,2)
julia> grid, m_index = smolyak_grid(chebyshev_extrema,2,[2,1])
julia> grid, m_index = smolyak_grid(chebyshev_extrema,2,2,[3.0 1.5; 2.0 0.5])
julia> grid, m_index = smolyak_grid(chebyshev_extrema,2,[2,2],[3.0 1.5; 2.0 0.5])
```
