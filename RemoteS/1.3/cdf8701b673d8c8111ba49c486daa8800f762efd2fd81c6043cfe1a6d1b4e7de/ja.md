```
Irgb = truecolor(bndR, bndG, bndB)
```

3つのLandsat8/Sentinel2 UINT16 GMT画像またはそれらのバンドのファイル名を取得し、自動ヒストグラムストレッチを適用してRGB真色画像を構成します。

UInt8 RGB GMT画像を返します。

```
Irgb = truecolor(cube::GMTImage, bands::Vector{Int})
```

マルチレイヤーGMT画像`cube`のレイヤーから、ベクトル'bands'に渡された3つのバンドのRGB合成を作成します。

自動ストレッチされたUInt8 RGB GMT画像を返します。

```
Irgb = truecolor(cube::String, [bands::Vector{Int}], [bandnames::Vector{String}], [raw=false])
```

UInt16マルチレイヤー配列を保持する`cube`ファイルから3つのバンドのRGB合成を作成します（通常は`cutcube`で作成されます）。バンドの選択は`bands`ベクトルで行うことができ、その場合は"Band[k]"という名前のバンドを検索するか、バンドの説明に`bandnames`の内容が含まれているかを確認します。`bands`または`bandnames`が使用されていない場合は、作成された`bandnames=["red", "green", "blue"]`を検索します。

自動ストレッチされたUInt8 RGB GMT画像または、`raw`オプションが`true`に設定されている場合はGMTimage{UInt16,3}を返します。

```
Irgb = truecolor(cube::GMTgrid, [bands|layers::Vector{Int}], [bandnames::Vector{String}], [type=UInt8])
```

Float32マルチレイヤー配列を保持する`cube`ファイルから3つのバンドのRGB合成を作成します。バンドの選択は`bands`ベクトルで行うことができ、その場合は"Band[k]"という名前のバンドを検索するか、バンドの説明に`bandnames`の内容が含まれているかを確認します。`bands`または`bandnames`が使用されていない場合は、作成された`bandnames=["red", "green", "blue"]`を検索します。

デフォルトでは、バンドを0-255にスケーリングします。`type=UInt16`を使用して、バンドを0-65535にスケーリングします。これは、ヒストグラムストレッチを実行するための良い制限を推測する際にのみ重要です。

### 例:

`cube`ファイル"LC08__cube.tiff"のデータからRGB合成を作成します。

```julia
I = truecolor("LC08__cube.tiff");
```
