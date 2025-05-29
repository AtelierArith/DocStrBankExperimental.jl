```
FourierDualDomain(imgdomain::AbstractSingleDomain, visdomain::AbstractSingleDomain, algorithm)
```

画像ドメインと可視ドメインに存在するグリッドのセットを構築します。グリッド間の変換は、`algorithm`によって指定され、これは`VLBISkyModels.FourierTransform`のサブタイプです。

# 引数

  * `imgdomain`: 画像ドメイングリッド
  * `visdomain`: 可視ドメイングリッド
  * `algorithm`: 使用するフーリエ変換アルゴリズム。リストについては`subtypes(VLBISkyModels.FourierTransform)`を参照してください。
