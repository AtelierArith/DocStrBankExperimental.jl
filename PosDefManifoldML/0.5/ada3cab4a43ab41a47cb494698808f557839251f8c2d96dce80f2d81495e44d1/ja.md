```julia
function binaryloss(yTrue::IntVector, yPred::IntVector)
```

真のラベルのベクトル `yTrue` と予測されたラベルのベクトル `yPred` に基づくバイナリエラーロス。これらの2つのベクトルは同じサイズでなければなりません。対応するラベルが異なる場合、エラーロスは1、そうでない場合は0です。ブール値のベクトル、すなわち `BitVector` を返します。

**参照** [`predict`](@ref).

**例**

```julia
using PosDefManifoldML, Random
dummy1, dummy2, yTr, yPr=gen2ClassData(2, 10, 10, 10, 10, 0.1);
shuffle!(yPr)
[yTr yPr binaryloss(yTr, yPr)]
```
