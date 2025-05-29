```
correlation(ito::ItoSet, index1::Integer, index2::Integer)
correlation(ito::ItoSet, brownian_id1::Symbol, brownian_id2::Symbol)
```

`ItoSet`内のブラウン運動間の相関を取得します。

### 入力

  * `ito` - 相関を求める2つのイートに対する`ItoSet`。
  * `index1`または`brownian_id1` - 最初のイート積分のインデックス/キー。
  * `index2`または`brownian_id2` - 2番目のイート積分のインデックス/キー。

### 戻り値

  * スカラー
