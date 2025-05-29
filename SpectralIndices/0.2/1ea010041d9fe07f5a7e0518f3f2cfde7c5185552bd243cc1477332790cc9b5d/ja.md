```
PlatformBand(platform_band::Dict{String, Any})
```

この構造体は、特定のセンサーまたはプラットフォームの特定のバンドに関する情報を提供します。

# 引数

  * `platform_band::Dict{String, Any}`: 次のキーを持つ辞書：

      * `"platform"`: プラットフォームまたはセンサーの名前。
      * `"band"`: 特定のプラットフォームのバンド番号または名前。
      * `"name"`: 特定のプラットフォームのバンドの説明または名前。
      * `"wavelength"`: 特定のプラットフォームのバンドの中心波長（nm単位）。
      * `"bandwidth"`: 特定のプラットフォームのバンドの帯域幅（nm単位）。

# 戻り値

指定されたバンド情報を含む `PlatformBand` オブジェクト。

# 例

```julia-repl
platform_band_dict = Dict(
    "platform" => "Sentinel-2A",
    "band" => "B2",
    "name" => "Blue",
    "wavelength" => 492.4,
    "bandwidth" => 66.0
)

platform_band = PlatformBand(platform_band_dict)
```

または、提供されたプラットフォームの辞書に直接アクセスする：

```julia-repl
julia> bands["B"].platforms["sentinel2a"]

```

```julia-repl
julia> bands["B"].platforms["sentinel2a"].wavelength

```
