```
struct HexagonBinner{M, CRS}
```

2次元の`Polygon`を正六角形のカバーでビン分けします。

最終的なビンの数は、要求された数とわずかに異なる場合があります。

### フィールド

  * `boundary`: [`Boundary`](@ref)オブジェクト。
  * `bins`: [`Bins`](@ref)オブジェクト。
  * `idx2pos`: ベクトルで、`idx2pos[i]`は、データなしおよび切断されたビンを削除する前にラベル付けされたビン`i`の位置（ビン内）を示します。このビンが削除された場合、`idx2pos[i] == nothing`となります。

### コンストラクタ

```
HexagonBinner(nbins, boundary; hardclip = true)
```
