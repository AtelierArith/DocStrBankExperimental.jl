TriMesh(mesh :: Mesh*ptr*C, vor :: Mesh*ptr*C, mesh_info :: String) 

TriMeshの外部コンストラクタ。`ccall(...)`によってTriangleライブラリから返される構造体を読み取ります。ポインタが`C_NULL`でない場合、メッシュデータの周りにJulia配列をラップします。
