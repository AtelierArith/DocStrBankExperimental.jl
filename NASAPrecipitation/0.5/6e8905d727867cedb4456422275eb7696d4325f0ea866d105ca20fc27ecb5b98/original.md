```
setup(;
    login     :: AbstractString = "",
    password  :: AbstractString = "",
    overwrite :: Bool = false
)
```

Function that sets up your .dodsrc and .netrc files for you.  If you do not provide the keyword arguments for `login` and `password`, the .netrc file will not be created.

# Keyword arguments

  * `login` : Your Earthdata username.  You need to specify both `login` and `password` arguments.
  * `password` : Your Earthdata password.  You need to specify both `login` and `password` arguments.
  * `overwrite` : If `true`, overwrite existing `.dodsrc` and `.netrc` files with the data provided.
