```
G = mesh_from_gmsh(pth)
G = mesh_from_gmsh()
G = mesh_from_gmsh(pth; verbose = true)
```

Gmshファイルを解析し、Jutul `UnstructuredMesh`（3Dのみ）を返します。Gmsh.jlパッケージがロードされている必要があります。`pth`にパスが提供されていない場合、Gmshの状態を手動で管理していると見なされ、Gmsh内の現在選択されているメッシュが使用されます。GmshはGPLライセンスの下で提供されていますが、著者から別のタイプのライセンスを取得している場合はこの限りではありません。
