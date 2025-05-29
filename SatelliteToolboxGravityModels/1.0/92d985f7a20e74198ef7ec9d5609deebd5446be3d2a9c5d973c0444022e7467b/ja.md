```
fetch_icgem_file(url::AbstractString; kwargs...) -> String
fetch_icgem_file(model::Symbol; kwargs...) -> String
```

`url`からICGEMファイルを取得し、関数[`GravityModels.load`](@ref)で解析するためのファイルパスを返します。ファイルがすでに存在する場合、キーワード`force = true`が渡されない限り再ダウンロードされることはありません。

URLの代わりにシンボルを渡すことで、事前に設定された重力場モデルを取得できます。サポートされている値は次のとおりです：

  * `:EGM96`: 1996年の地球重力モデル。
  * `:EGM2008`: 2008年の地球重力モデル。
  * `:JGM2`: ジョイント重力モデル2。
  * `:JGM3`: ジョイント重力モデル3。

# 例

```julia-repl
julia> fetch_icgem_file(:EGM96)
[ Info: 'EGM96.gfc'というICGEMファイルを'http://icgem.gfz-potsdam.de/getmodel/gfc/971b0a3b49a497910aad23cd85e066d4cd9af0aeafe7ce6301a696bed8570be3/EGM96.gfc'からダウンロードしています...
"/Users/ronan.arraes/.julia/scratchspaces/bd9e9728-6f7b-4d28-9e50-c765cb1b7c8c/icgem/EGM96.gfc"

julia> fetch_icgem_file(:EGM96)
"/Users/ronan.arraes/.julia/scratchspaces/bd9e9728-6f7b-4d28-9e50-c765cb1b7c8c/icgem/EGM96.gfc"
```
