サーモオブジェクトを作成する関数。この関数はtherm.datファイルを読み込み、理想気体オブジェクトに基づいて内容を解析し、サーモデータオブジェクトを作成します。この関数はSpeciesThermoObjを返します。

# 使用法:

```
create_thermo(species::Array{T,1}, thermo_file::AbstractString )
```

  * species  : 種の名前の配列
  * thermo_file : パスを含むサーモファイルの名前
