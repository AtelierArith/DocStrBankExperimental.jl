```
ngon(centerpos, radius, sides=5, orientation=0;
    action=:none,
    vertices=false,
    reversepath=false)
```

点 `centerpos` を中心とした正多角形を描画します。

外接円の半径 `radius` を持つ、`x`、`y` を中心とした正 n 辺形の頂点を求めます。

多角形は反時計回りに構築され、最初の頂点は正の x 軸の下に描かれます。

生のポイントだけが必要な場合は、キーワード引数 `vertices=true` を使用してください。これにより、ポイントの配列が返されます。比較してみましょう：

```julia
julia> ngon(0, 0, 4, 4, 0, vertices=true) # 多角形のポイントを返します：
4-element Vector{Point}:
 Point(2.4492935982947064e-16, 4.0)
 Point(-4.0, 4.898587196589413e-16)
 Point(-7.347880794884119e-16, -4.0)
 Point(4.0, -9.797174393178826e-16)
```

一方で

```julia
ngon(0, 0, 4, 4, 0, :close) # 多角形を描画します
```
