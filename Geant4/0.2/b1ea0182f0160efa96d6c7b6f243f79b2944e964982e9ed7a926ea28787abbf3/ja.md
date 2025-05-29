```
G4JLMagneticField(name::String, data::DATA; <keyword arguments>) where DATA<:G4JLGeneratorData
```

名前と関連するDATA構造を持つG4JLMagneticFieldを作成します

# 引数

  * `name::String`: 磁場の名前
  * `data::DATA`: 磁場に関連するデータ構造
  * `getfield_method=nothing`: ユーザー提供の`getfield`関数で、シグネチャは次のとおりです: `(result::G4ThreeVector, position::G4ThreeVector, ::DATA)`
