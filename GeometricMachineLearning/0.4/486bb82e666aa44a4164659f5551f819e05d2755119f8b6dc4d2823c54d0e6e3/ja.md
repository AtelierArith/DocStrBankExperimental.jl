```
onehotbatch(target)
```

整数のベクトルのワンホットバッチエンコーディングを実行します: $input\in\{0,1,\ldots,9\}^\ell$. 

出力は形状 $10\times1\times\ell$ のテンソルです。

入力が $0$ の場合、この関数は次のように生成します:

$$
0 \mapsto \begin{bmatrix} 1 & 0 & \ldots & 0 \end{bmatrix}^T.
$$

より抽象的な言い方をすると: $i \mapsto e_i$.

# 例

```jldoctest
using GeometricMachineLearning: onehotbatch

target = [0]
onehotbatch(target)

# 出力

10×1×1 Array{Int64, 3}:
[:, :, 1] =
 1
 0
 0
 0
 0
 0
 0
 0
 0
 0
```
