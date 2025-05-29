```
t8_stash_joinface
```

The face-connection information that is stored before a cmesh is committed.

| Field       | Note                                                                  |
|:----------- |:--------------------------------------------------------------------- |
| id1         | The global tree id of the first tree in the connection.               |
| id2         | The global tree id of the second tree. We ensure id1<=id2.            |
| face1       | The face number of the first of the connected faces.                  |
| face2       | The face number of the second face.                                   |
| orientation | The orientation of the face connection.  # See also t8_cmesh_types.h. |
