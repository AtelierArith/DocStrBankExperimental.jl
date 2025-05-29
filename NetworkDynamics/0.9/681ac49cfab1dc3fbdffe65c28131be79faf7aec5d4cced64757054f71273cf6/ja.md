```
vidxs([inpr], components=:, variables=:) :: Vector{EIndex}
```

エッジのためのシンボリックインデックスのベクトルを生成します。

  * `inpr`: 名前のマッチングまたは `:` アクセスのためにのみ必要です。Network、sol、prob、...
  * `components`: 数/ベクトル、`:`、`Symbol`（名前が一致）、`String`/`Regex`（名前が含まれる）
  * `variables`: シンボル/数/ベクトル、`:`、`String`/`Regex`（すべてのシンボルを含む）

例:

```
eidxs(nw)                # すべてのエッジ状態インデックス
eidxs(1:2, :u)           # [EIndex(1, :u), EIndex(2, :u)]
eidxs(nw, :, [:u, :v])   # [EIndex(i, :u), EIndex(i, :v) for i in 1:ne(nw)]
eidxs(nw, "FlowEdge", :) # 名前に "FlowEdge" を含むすべてのエッジのすべてのシンボル
```
