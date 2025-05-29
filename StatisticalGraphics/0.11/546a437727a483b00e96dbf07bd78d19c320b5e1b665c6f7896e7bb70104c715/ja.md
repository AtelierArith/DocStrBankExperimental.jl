```
sggrid(sgps...; opts...)
```

SGプロットのコレクションをグリッド内に配置します。`opts...`は`sggrid`に渡すことができる追加のキーワード引数を指します。

# キーワード引数

## プロットの外観

  * `align`: プロットの整列方法を決定します。`:all`、`:each`、または`:none`のいずれかです。デフォルト: `:none`
  * `backcolor`: 背景色。
  * `bordercolor`: プロットの境界の色。デフォルト: `:transparent`
  * `bounds`: `:full`または`:flush`のいずれか。詳細については`vega`のドキュメントを参照してください。デフォルト: `:full`
  * `center`: 行と列のセンタリング、それぞれ。デフォルト: `Bool[0, 0]`
  * `columns`: 作成する列の数。
  * `columnspace`: 列間のスペース。デフォルト: `0`
  * `rowspace`: 行間のスペース。デフォルト: `0`
