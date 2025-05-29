```
meshdata(self::ImageMesher)
```

Retrieve the current mesh data.

The three arrays returned are: 

  * `t` = array of tetrahedral connectivities, one row per element,
  * `v` = array of coordinates of the nodes, one row per vertex,
  * `tmid` = array of material identifiers, one per element.
