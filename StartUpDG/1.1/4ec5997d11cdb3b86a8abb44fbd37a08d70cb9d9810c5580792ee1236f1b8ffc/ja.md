```
function read_Gmsh_2D_v4(filename, options)
```

三角形 GMSH 2D .msh ファイルを読み込みます。

# 出力

これは、グループ化が選択されているかどうかによります。

  * 戻り値: (VX, VY), EToV
  * 戻り値: (VX, VY), EToV, グループ化

# サポートされているフォーマットと機能:

  * バージョン 4.1   '物理グループサポート   'グループ ID の再マッピング

## グループ化の適用

波動方程式をモデル化する際、ドメイン全体で波速を変化させたい場合があります。Gmsh で物理グループを割り当てることで、.msh ファイルをインポートする際にそのグループを維持できます。インポートされた各要素は物理グループのメンバーになります。

```julia
VXY, EToV = read_Gmsh_2D_v4("eulerSquareCylinder2D.msh")
VXY, EToV = read_Gmsh_2D_v4("eulerSquareCylinder2D.msh",false)
VXY, EToV, grouping = read_Gmsh_2D_v4("eulerSquareCylinder2D.msh", true)

option = MeshImportOption(true)
VXY, EToV, grouping = read_Gmsh_2D_v4("eulerSquareCylinder2D.msh", option)
```

https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format

注意: バージョン 4 フォーマットは、より詳細なブロックデータフォーマットを持っており、これによりより複雑なパーサーが必要になります。
