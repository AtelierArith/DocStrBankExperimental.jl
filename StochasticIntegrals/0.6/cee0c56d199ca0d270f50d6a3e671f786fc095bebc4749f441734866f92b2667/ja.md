```
SimpleCovariance
```

`SimpleCovariance` 構造体を作成します。これは `ForwardCovariance` の簡略版であり、定数の `ItoIntegral` 用に設計されています（したがって、相関を再計算する必要はありません）。この計算の節約が唯一の利点です - `ForwardCovariance` はより一般的です。これは `ForwardCovariance` と同じ要素を含みます：

  * Itoset
  * 共分散期間が始まる時刻。
  * 共分散期間が延びる時刻。

コンストラクタでは、次の項目が生成され、オブジェクトに保存されます：

  * 共分散行列
  * 共分散行列のラベル。
  * 共分散行列のコレスキー分解。
  * 共分散行列の逆行列。
  * 共分散行列の行列式。

コンストラクタは次の通りです：

```
SimpleCovariance(ito_set_::ItoSet, from_::Real, to_::Real;
     calculate_chol::Bool = true, calculate_inverse::Bool = true, calculate_determinant::Bool = true)
```
