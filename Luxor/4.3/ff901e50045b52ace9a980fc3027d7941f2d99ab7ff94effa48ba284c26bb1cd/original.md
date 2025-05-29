```
textextents(str)
```

Return an array of six Float64s containing the measurements of the string `str` when set using the current font settings (Toy API):

1. x_bearing
2. y_bearing
3. width
4. height
5. x_advance
6. y_advance

The x and y bearings are the displacement from the reference point to the upper-left corner of the bounding box. It is often zero or a small positive value for x displacement, but can be negative x for characters like "j"; it's almost always a negative value for y displacement.

The width and height then describe the size of the bounding box. The advance takes you to the suggested reference point for the next letter. Note that bounding boxes for subsequent blocks of text can overlap if the bearing is negative, or the advance is smaller than the width would suggest.

Example:

```
textextents("R")
```

returns

```
[1.18652; -9.68335; 8.04199; 9.68335; 9.74927; 0.0]
```
