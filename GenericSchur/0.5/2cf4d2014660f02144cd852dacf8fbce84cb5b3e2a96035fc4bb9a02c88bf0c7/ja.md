```
eigvalscond(S::GeneralizedSchur, nsub) => pl, pr
```

左/右部分空間に関連する射影子の近似逆ノルムを計算します。これは、`S`の先頭の `nsub`×`nsub` ブロックに関連しています。興味のある固有値を選択するために `ordschur` を使用します。

関連する固有値の平均絶対誤差の近似的な上限は `ϵ * norm(vcat(A,B)) / pl` です。詳細については LAPACK のドキュメントを参照してください。
