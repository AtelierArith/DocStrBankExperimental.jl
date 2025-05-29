```
LDataSet <: AbstractDataSet
```

パラメータ化された名前パターンを持つデータセットを生成するためのテンプレート。

# フィールド

  * `format`: データセット名のフォーマット文字列パターン
  * `data`: 変数パターンの辞書
  * `metadata`: 追加のメタデータ

# 例

```julia
using SPEDAS.MMS

# FPIデータセット仕様にアクセス
lds = mms.datasets.fpi_moms

# 特定のパラメータを持つ具体的なデータセットを作成
ds = DataSet(lds; probe=1, data_rate="fast", data_type="des")
```

フォーマット文字列と変数パターンは、具体的な`DataSet`を作成する際に実際の値に置き換えられるプレースホルダー `{probe}`、`{data_rate}` のようなものを使用します。
