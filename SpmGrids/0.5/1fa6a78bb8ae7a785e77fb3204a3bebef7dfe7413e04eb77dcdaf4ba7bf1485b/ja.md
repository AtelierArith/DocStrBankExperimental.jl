```
load_grid(images::Vector{<:SpmImage}, by::Function=im -> im.z
name::AbstractString="Z", unit::AbstractString="m";
only_overlap::Bool=false, header_only::Bool=false)::SpmGrid
```

画像のスタックからグリッドを読み込みます。スイープ信号は`by`引数で指定され、`name`と`unit`も指定されます。最初の画像がピクセル密度と利用可能なチャンネルを決定します。ここでは、逆方向のチャンネルが画像の逆スキャン方向に関連付けられます。理想的には、すべての画像は同じピクセル密度と記録されたチャンネルを持つべきです。`only_overlap`がtrueの場合、すべての画像で重なっているピクセルのデータのみが返されます。`header_only`がtrueの場合、ヘッダーのみが作成されます。
