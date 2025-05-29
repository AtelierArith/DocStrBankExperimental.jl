```
vidxs([inpr], components=:, variables=:) :: Vector{VIndex}
```

頂点のための記号インデックスのベクトルを生成します。

  * `inpr`: 名前のマッチングまたは `:` アクセスのためにのみ必要です。Network、sol、prob、...
  * `components`: 数/ベクトル、`:`、`Symbol`（名前が一致）、`String`/`Regex`（名前が含まれる）
  * `variables`: シンボル/数/ベクトル、`:`、`String`/`Regex`（すべてのシンボルを含む）

例:

```
vidxs(nw)                 # すべての頂点状態インデックス
vidxs(1:2, :u)            # [VIndex(1, :u), VIndex(2, :u)]
vidxs(nw, :, [:u, :v])    # [VIndex(i, :u), VIndex(i, :v) for i in 1:nv(nw)]
vidxs(nw, "ODEVertex", :) # 名前に "ODEVertex" を含むすべての頂点のすべてのシンボル
```
