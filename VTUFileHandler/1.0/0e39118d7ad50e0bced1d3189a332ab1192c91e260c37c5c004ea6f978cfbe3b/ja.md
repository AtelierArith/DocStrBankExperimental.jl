```
VTUFile(name::String)
```

VTUファイルを読み込みます。`set_uncompress_keywords`と`set_interpolation_keywords`を使用して、適切なフィールド名を設定するのを忘れないでください。

# コンストラクタ

  * `name::String`: vtuファイルへのパス

# フィールド

  * `name::String`: vtuファイルへのパス; ファイル書き込みの宛先
  * `xmlroot::AbstractXMLElement`: XML表現のVTUファイル
  * `dataarrays::Vector{AbstractXMLElement}`: VTUファイルの`DataArray`タグを持つすべてのXML要素を含むベクター
  * `headertype::Union{Type{UInt32},Type{UInt64}}`: ヘッダーのタイプ
  * `offsets::Vector{Int}`: 圧縮された追加データ内の各フィールドデータのオフセット
  * `data::VTUData`: [`VTUData`](@ref)を含むコンテナ
  * `compressed_dat::Bool` : データが圧縮されている場合はTrue

# 例

```julia
set_uncompress_keywords("temperature","points")
set_interpolation_keywords("temperature")
vtufile = VTUFile("./path-to-vtu/example.vtu");
```
