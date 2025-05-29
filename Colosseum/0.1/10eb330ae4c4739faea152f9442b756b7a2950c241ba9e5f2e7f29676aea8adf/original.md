Set segmentation ID for specific objects

See https://microsoft.github.io/AirSim/image_apis/#segmentation for details

Args:     mesh*name (str) Name of the mesh to set the ID of (supports regex)     object*id (int) Object ID to be set, range 0-255

```
                    RBG values for IDs can be seen at https://microsoft.github.io/AirSim/seg_rgbs.txt
is_name_regex (bool, optional) Whether the mesh name is a regex
```

Returns:     bool: If the mesh was found
