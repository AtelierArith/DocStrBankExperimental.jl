```
p8est_iter_corner_side
```

| Field    | Note                                                |
|:-------- |:--------------------------------------------------- |
| treeid   | the tree that contains *quad*                       |
| corner   | which of the quadrant's corners touches this corner |
| is_ghost | boolean: local (0) or ghost (1)                     |
| quadid   | the index in the tree or ghost array                |
| faces    | internal work data                                  |
| edges    |                                                     |
