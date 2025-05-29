Runtime Swap Texture API

See https://microsoft.github.io/AirSim/retexturing/ for details

Args:     tags (str) string of "," || ", " delimited tags to identify on which actors to perform the swap     tex_id (int, optional) indexes the array of textures assigned to each actor undergoing a swap

```
                        If out-of-bounds for some object's texture set, it will be taken modulo the number of textures that were available
component_id (int, optional)
material_id (int, optional)
```

Returns:     list[str]: List of objects which matched the provided tags and had the texture swap perfomed
