```
Band(band::Dict{String, Any})
```

特定のバンドと対話するための`Band`オブジェクトを構築します。これは、Awesome Spectral Indicesリストの必要なバンドのリストに関連しています。

# 引数

  * `band::Dict{String, Any}`: 次のキーを持つバンド情報を含む辞書：

      * `"short_name"`: バンドの短い名前。
      * `"long_name"`: バンドの説明または名前。
      * `"common_name"`: STACの電気光学拡張仕様に従ったバンドの一般的な名前。
      * `"min_wavelength"`: バンドのスペクトル範囲の最小波長（nm単位）。
      * `"max_wavelength"`: バンドのスペクトル範囲の最大波長（nm単位）。
      * `"platforms"`: このバンドに関連するプラットフォーム情報の辞書。

# 戻り値

指定されたバンドを表す`Band`オブジェクト。

# 例

```julia-repl
julia> bands["B"]
band_dict = Dict{String, Any}(
    "short_name" => "B",
    "long_name" => "Blue",
    "common_name" => "Blue",
    "min_wavelength" => 450.0,
    "max_wavelength" => 495.0,
    "platforms" => Dict{String, Any}(
        "sentinel2a" => PlatformBand(...),  # PlatformBandコンストラクタの詳細はここに
        "sentinel2b" => PlatformBand(...),  # PlatformBandコンストラクタの詳細はここに
        # 必要に応じて他のプラットフォームを追加
    )
)

band = Band(band_dict)
```

または、提供されたバンドを使用して

```julia-repl
julia> bands["B"].long_name

```
