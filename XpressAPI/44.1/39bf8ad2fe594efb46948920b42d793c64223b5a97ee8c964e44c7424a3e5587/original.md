```
XPRS_MAXTREEFILESIZE
```

The maximum size, in megabytes, to which the tree file may grow, or 0 for no limit. (integer)

When the tree file reaches this limit, a second tree file will be created. Useful if you are using a filesystem that puts a maximum limit on the size of a file.

Default value: `0`

Domain: 0~+INF
