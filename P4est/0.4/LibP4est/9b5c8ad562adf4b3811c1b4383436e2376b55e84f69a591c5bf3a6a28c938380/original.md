```
p8est_tree
```

The `p8est` tree datatype

| Field            | Note                                                              |
|:---------------- |:----------------------------------------------------------------- |
| quadrants        | locally stored quadrants                                          |
| first_desc       | first local descendant                                            |
| last_desc        | last local descendant                                             |
| quadrants_offset | cumulative sum over earlier trees on this processor (locals only) |
| maxlevel         | highest local quadrant level                                      |
