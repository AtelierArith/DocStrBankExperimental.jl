```
PluckerMotion(data::AbstractVector)
```

Plucker運動ベクトルのインスタンスを作成します。

$$
v = \begin{bmatrix} \Omega \\ U \end{bmatrix}
$$

`data`のベクトルを使用します。`data`の長さが6の場合、3次元運動ベクトルを作成し、最初の3つのエントリは回転成分`\Omega`を構成し、最後の3つのエントリは並進成分`U`を構成するものとします。`data`の長さが3の場合、2次元運動ベクトルを作成し、`data`の最初のエントリが回転成分を表し、2番目と3番目のエントリがxおよびyの並進成分を表すと仮定します。
