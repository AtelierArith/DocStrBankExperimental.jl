ウィジェットは、提供された要素の配列から `StructBond` または結果の形式 `transformed_value(f, ::StructBond)` のいずれかのサブウィジェットを選択するためのものです。

これは、表示するサブウィジェットを選択するためのドロップダウンを表示し、`@bind` と組み合わせることで `StructBondSelect` 出力を生成するために使用されます。

以下の拡張ヘルプには、GIFの例や [docs page](https://disberd.github.io/PlutoExtras.jl/stable/structbond/#StructBondSelect) に動画のものがあります。

## コンストラクタ

```julia
StructBondSelect(els::Vector[, selectors::Vector{String}]; description = "StructBondSelect", default_idx = 1, selector_text = "Selector")
```

### 引数

  * `els`: `StructBond` または `transformed_value(f, ::StructBond)` 要素のベクター。
  * `selectors`: 選択に使用される名前としての文字列のベクター。提供されない場合、提供された `StructBond` 要素の `description` から名前が取られます。

### キーワード引数

  * `description`: ウィジェットの説明として使用される文字列で、デフォルトは `"StructBondSelect"` です。
  * `default_idx`: デフォルトで表示/出力される要素のインデックスで、デフォルトは `1` です。
  * `selector_text`: セレクタードロップダウンの横に表示されるテキストで、デフォルトは `"Selector"` です。

# 拡張ヘルプ

視覚的な例についてはこの画像を参照してください: ![structbondselect-example](https://private-user-images.githubusercontent.com/12846528/435671705-91ff7e4a-2b4c-4688-8f2b-ea53a622dd04.gif?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDUyNDAzMTgsIm5iZiI6MTc0NTI0MDAxOCwicGF0aCI6Ii8xMjg0NjUyOC80MzU2NzE3MDUtOTFmZjdlNGEtMmI0Yy00Njg4LThmMmItZWE1M2E2MjJkZDA0LmdpZj9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA0MjElMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwNDIxVDEyNTMzOFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTYwMmI1ZTYyNGQ1NDMyZGNlZTE3NzljMjJlNWQyOTU5ODUyMDdiODkzYWQxNDRmNzEwZjYxZmEzNTgwZDUyYmEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.L9eC42c4-Gz0tpjzGgF95LhOvcrGAEPOkJ71HhiICrs)

また、[`StructBond`](@ref)、[`@NTBond`](@ref) も参照してください。
