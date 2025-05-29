```
openkey(basekey::RegKey, path::AbstractString, accessmask::UInt32=KEY_READ)
```

Open a registry key at `path` relative to `basekey`. `accessmask` is a bitfield. `\` is used as a path separator.
