```
ForwardCovariance
```

`ForwardCovariance`構造体を作成します。これには以下が含まれます：

  * `Itoset`。
  * 共分散期間が始まる時刻。
  * 共分散期間が延長される時刻。

コンストラクタでは、以下の項目が生成され、オブジェクトに保存されます：

  * 共分散行列
  * 共分散行列のラベル。
  * 共分散行列のコレスキー分解。
  * 共分散行列の逆行列。
  * 共分散行列の行列式。

コンストラクタは次の通りです：

```
ForwardCovariance(ito_set_::ItoSet, from_::Real, to_::Real;
                  calculate_chol::Bool = true, calculate_inverse::Bool = true, calculate_determinant::Bool = true)
ForwardCovariance(ito_set_::ItoSet, from::Union{Date,DateTime}, to::Union{Date,DateTime})
ForwardCovariance(old_ForwardCovariance::ForwardCovariance, from::Real, to::Real)
ForwardCovariance(old_ForwardCovariance::ForwardCovariance, from::Union{Date,DateTime}, to::Union{Date,DateTime})
```
