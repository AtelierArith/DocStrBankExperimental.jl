```
MeshImportOptions
```

This struct allows the user to opt for supported features when importing a Gmsh 4.1 .msh file.

## Support

  * grouping::Bool | On import would you like to include physical group assignements of 2D elements?
  * remap_group_name::Bool | On import would you like to maintain or remap physical group ID? Remap results in groupIds in the range 1:number_group_ids.
