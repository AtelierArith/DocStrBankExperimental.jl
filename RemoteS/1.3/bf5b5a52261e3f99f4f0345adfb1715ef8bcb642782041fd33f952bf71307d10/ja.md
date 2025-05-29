```
subcube(cube::String; bands=Int[], bandnames=String[], layers=Int[])
```

`cube`から`bands`ベクターにあるレイヤーを持つサブキューブを抽出します。この場合、"Band band[k]"という名前のバンドを検索するか、`bandnames`文字列ベクターにある説明に部分的に一致する（大文字と小文字を区別しない）名前のバンドを検索します。つまり、`bands`と`bandnames`のオプションは、バンドの説明がある「キューブ」でのみ使用できます。`layers`オプションは、`layer`ベクターにリストされた`cube`の平面を盲目的に抽出します。

GMTimageを返します。

```
subcube(cube::Union{GMT.GMTimage{UInt16, 3}, AbstractArray{<:AbstractFloat, 3}}; bands=Int[], bandnames=String[], layers=Int[])
```

メモリ内のキューブから同じことを行います。入力タイプと同じタイプを返します。ビューはなく、データのコピーです。

### 例

`cutcube`で作成したLandsat 8キューブから赤、緑、青のレイヤーを抽出します。

```
Irgb = subcube("LC08__cube.tiff", bandnames = ["red", "green", "blue"])
```
