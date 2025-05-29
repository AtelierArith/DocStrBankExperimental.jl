```
serialize(filename::AbstractString, structures::AbstractVector{<:ProteinStructure})
```

`ProteinStructure`オブジェクトのベクターをJLD2ファイルにシリアライズします。この関数は新しい`ProteinStructureStore`を作成し、入力ベクター内の各構造をそれに書き込みます。各構造は、その名前をキーとして使用して保存されます。
