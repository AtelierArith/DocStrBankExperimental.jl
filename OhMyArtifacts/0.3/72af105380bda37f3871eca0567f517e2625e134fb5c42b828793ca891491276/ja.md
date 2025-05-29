```
download_my_artifact!([downloadf::Function = Downloads.download], url, name::AbstractString, artifacts_toml::String;
                     force_bind::Bool = false, bind_metadata = nothing, downloadf_kwarg...)
```

ダウンロード、作成、バインドを一緒に行い、コンテンツハッシュを返す便利な関数です。ダウンロード関数 `downloadf` は2つの位置引数を取る必要があります（すなわち、`downloadf(url, dest; downloadf_kwarg...)`）。`force_bind` が `true` の場合、既存のバインディングを上書きします。

関連情報: [create*my*artifact](@ref), [bind*my*artifact!](@ref)
