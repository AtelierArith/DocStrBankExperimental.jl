```
get_scene_id(scene)
```

提供されたシーンのユニークな識別子を検索します。

# パラメータ

  * `scene`: 検索するSentinelシーンの名前。

# 戻り値

提供されたシーンをダウンロードするためのユニークな識別子。

# 例

```julia
julia> scene = "S2B_MSIL2A_20200804T183919_N0500_R070_T11UPT_20230321T050221";

julia> get_scene_id(scene)
"29f0eaaf-0b15-412b-9597-16c16d4d79c6"
```
