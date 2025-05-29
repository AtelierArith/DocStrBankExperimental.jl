```
simple_cross(lv_x, lv_y; lh_x=lv_y, lh_y=lv_x)
```

A simple cross centered at the origin. The only required inputs are `lv_x` and `lv_y`, the length of the vertical strip along the x and y directions, respectively. The corresponding dimensions of the horizontal strip are given as keyword arguments, with the defaults producing identical horizontal and vertical strips.

```
_ |<--------- lh_x ----------->|
|            |▓▓▓▓|
|            |▓▓▓▓|
lv_y         |▓▓▓▓|
|            |<  >| lv_x
|            |▓▓▓▓|
| |▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓| lh_y
| |▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓|
|            |▓▓▓▓|
|            |▓▓▓▓|
|            |▓▓▓▓|
|            |▓▓▓▓|
_            |▓▓▓▓|
```
