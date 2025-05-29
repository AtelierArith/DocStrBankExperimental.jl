```
struct LineBinner{M, CRS}
```

1次元の`Segment`（線分）を`nbins`個の等間隔のビンでビン分けします。

### フィールド

  * `boundary`: [`Boundary`](@ref)オブジェクト。
  * `bins`: [`Bins`](@ref)オブジェクト。
  * `idx2pos`: ベクトルで、`idx2pos[i]`は、データなしおよび切断されたビンを削除する前にラベル付けされたビン`i`の位置（ビン内）を示します。このビンが削除された場合、`idx2pos[i] == nothing`となります。

### コンストラクタ

```
LineBinner(nbins, boundary; hardclip = true)
```
