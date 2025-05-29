```
approximatefekete(basis, samples; base_ring=BigFloat) -> basis, samples
```

サンプルと対応する直交基底に基づいて近似フェケテ点を計算します。基底は、`samples`でサンプリングされた多項式で構成されています。

これにより、存在する場合は`basis`の次数順序が保持されます。
