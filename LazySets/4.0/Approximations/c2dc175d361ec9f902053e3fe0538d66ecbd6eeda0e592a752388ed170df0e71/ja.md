```
overapproximate(Z::AbstractZonotope, ::Type{<:HParallelotope},
                [indices]=1:dim(Z))
```

ゾノトピック集合を制約表現の中で平行トポスで上近似します。

### 入力

  * `Z`              – ゾノトピック集合
  * `HParallelotope` – 目標集合タイプ
  * `indices`        – （オプション; デフォルト: `1:dim(Z)`）平行トポスを構築する際に選択される生成子インデックス

### 出力

与えられたゾノトピック集合を平行トポスを用いて上近似したもの。

### アルゴリズム

このアルゴリズムは、[AlthoffSB10; Section 5](@citet)で議論された命題8に基づいています。
