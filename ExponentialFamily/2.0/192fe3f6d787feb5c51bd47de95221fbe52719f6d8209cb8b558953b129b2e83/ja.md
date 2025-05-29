```
JointNormal{D, S}
```

`JointNormal`は、正規分布変数の共同周辺のために使用される補助構造です。`JointNormal`は元の次元（ds）を持つベクトルを格納するため、統計は後で再分離できます。

特定の共同分布の成分を取得するには、`ExponentialFamily.getcomponent(joint, index)`を使用します。

# フィールド

  * `dist`: 共同分布（通常は大きな`MvNormal`分布ですが、個々の平均と共分散行列のタプルである場合もあります）
  * `ds`: 個々の`Normal`分布の元の次元を持つタプル
  * `ds[k] = (n,)` ここで `n` は整数で、サイズ `n` の多変量正規分布を示します
  * `ds[k] = ()` は単変量正規分布を示します
