```
mj_loadXML(filename, vfs, error, error_sz)
```

Parse XML file in MJCF or URDF format, compile it, return low-level model. If vfs is not NULL, look up files in vfs before reading from disk. If error is not NULL, it must have size error_sz.
