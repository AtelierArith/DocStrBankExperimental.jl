```
LobattoLegendreBasis([RealT = Float64,] polydeg::Integer)
```

多項式の次数 `polydeg` に対するノーダル・ロバット・レジェンドル基底を作成します。

特別な場合 `polydeg=0` では、DG法は有限体積法に簡略化されます。したがって、この関数はセルの中心点を単一のノードとして設定します。この例外的なケースは現在、TreeMesh のみでサポートされています！
