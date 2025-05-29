```
struct RectangleBinner{M, CRS}
```

2次元の`Polygon`を、矩形の厳密なカバーでビン分けします。矩形はできるだけ正方形に近いものが選ばれ、最終的なビンの数は要求された数とわずかに異なる場合があります。

### フィールド

  * `boundary`: [`Boundary`](@ref)オブジェクト。
  * `bins`: [`Bins`](@ref)オブジェクト。
  * `idx2pos`: ベクトルで、`idx2pos[i]`は、データなしおよび切断されたビンを削除する前にラベル`i`が付けられたビンの位置（ビン内）を示します。このビンが削除された場合、`idx2pos[i] == nothing`となります。

### コンストラクタ

```
RectangleBinner(nbins, boundary; hardclip = true)
```

`nbins`は次のいずれかです：

  * `Integer`の場合、`RectangleBinner`が構築され、`x`および`y`に沿ってボックスを比例配分し、ボックスの総数が`nbins`にできるだけ近くなるようにします。
  * `NTuple{2, Integer}`の場合、次元`i`は`nbins[i]`ビンを受け取ります。
  * `NTuple{2, AbstractVector}`の場合、`nbins[i]`は次元`i`のビンのエッジを定義します。
