```
struct HyperRectangleBinner{Dim, M, CRS}
```

`Dim`次元（`Dim ≥ 3`）のデータセットを、同一のハイパーレクタングルの厳密なカバーに基づいてビン分けします。

ハイパーレクタングルは、できるだけハイパーキューブに近いものとして選ばれます。

`HyperRectangleBinner`にはハードクリッピング機能はありません。ただし、データのないビンは、メインのウラム法計算で依然として削除されます。

最終的なビンの数は、要求された数よりも異なる（大きい）場合があります。

### フィールド

  * `boundary`: [`Boundary`](@ref) オブジェクト。
  * `bins`: [`Bins`](@ref) オブジェクト。
  * `idx2pos`: `idx2pos[i]`が、データのないビンや切断されたビンを削除する前にラベル付けされたビン`i`の位置（ビン内）を示すベクトル。もしこのビンが削除された場合、`idx2pos[i] == nothing`となります。
  * `ranges`: `ranges[i]`が次元`i`に沿ったビンのグリッドポイントを示す`AbstractRange`であるベクトル。

### コンストラクタ

```
HyperRectangleBinner(nbins, boundary)
```

`nbins`は次のように指定できます：

  * `Integer`の場合、この場合、`HyperRectangleBinner`は、全体のボックス数が`nbins`にできるだけ近くなるように、次元に沿ってボックスを比例配分しようとします。
  * `NTuple{Dim, Integer}`の場合、この場合、次元`i`は`nbins[i]`ビンを受け取ります。
