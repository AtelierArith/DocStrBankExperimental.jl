An MeshFileGeometry represents a mesh which is stored as the raw contents of a file, rather than as a collection of points and vertices. This is useful for transparently passing mesh files which we can't load in Julia directly to meshcat.

Supported formats:     * .stl (ASCII and binary)     * .obj     * .dae (Collada)

For .obj and .dae files, only a single mesh geometry will be loaded, and any material or texture properties will be ignored. To load an entire collection of objects (complete with materials and textures) from an .obj or .dae file, see MeshFileObject instead.
