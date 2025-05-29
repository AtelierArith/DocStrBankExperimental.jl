```
XPRS_TREECOMPRESSION
```

When writing nodes to the gloal file, the optimizer can try to use data-compression techniques to reduce the size of the tree file on disk. (integer)

The `TREECOMPRESSION` control determines the strength of the data-compression algorithm used; higher values give superior data-compression at the affect of decreasing performance, while lower values compress quicker but not as effectively. Where `TREECOMPRESSION` is set to 0, no data compression will be used on the tree file.

Default value: `2`

Domain: 0,1,2,3,4,5,6,7,8,9
