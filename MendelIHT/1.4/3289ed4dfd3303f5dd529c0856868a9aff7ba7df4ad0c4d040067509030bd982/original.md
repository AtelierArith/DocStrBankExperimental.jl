```
make_bim_fam_files(x::SnpArray, y, name::String)
```

Creates .bim and .bed files from a SnpArray. 

# Arguments:

  * `x`: A SnpArray (i.e. `.bed` file on the disk) for which you wish to create corresponding `.bim` and `.fam` files.
  * `name`: string that should match the `.bed` file (Do not include `.bim` or `.fam` extensions in `name`).
  * `y`: Trait vector that will go in to the 6th column of `.fam` file.
