TriMesh(mesh :: Mesh*ptr*C, vor :: Mesh*ptr*C, mesh_info :: String) 

Outer constructor for TriMesh. Read the struct returned by `ccall(...)` to Triangle library. Wrap a Julia arrays around mesh data if their pointer is not `C_NULL`.
