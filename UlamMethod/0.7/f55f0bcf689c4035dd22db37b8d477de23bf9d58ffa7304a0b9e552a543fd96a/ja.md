```
struct VoronoiBinner{Dim, M, CRS}
```

`Dim`次元のビン（`Dim ∈ (1, 2)`）データセットを、初期の軌道データ（すなわち`Trajectories.x0`）のk-meansクラスタリングによって生成された点のボロノイ分割に基づいてビン分けします。

### フィールド

  * `boundary`: [`Boundary`](@ref)オブジェクト。
  * `bins`: [`Bins`](@ref)オブジェクト。
  * `idx2pos`: ベクトルで、`idx2pos[i]`は、データなしおよび切断されたビンを削除する前にラベル付けされたビン`i`の位置（ビン内）を示します。このビンが削除された場合、`idx2pos[i] == nothing`となります。

### コンストラクタ

```
VoronoiBinner(nbins, boundary, traj; hardclip = true)
```
