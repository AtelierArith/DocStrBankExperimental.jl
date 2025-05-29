```
vis = Visualizer()
```

Construct a new MeshCat visualizer instance.

Useful methods:

```
vis[:group1] # get a new visualizer representing a sub-tree of the scene
setobject!(vis, geometry) # set the object shown by this visualizer's sub-tree of the scene
settransform!(vis, tform) # set the transformation of this visualizer's sub-tree of the scene
setvisible!(vis, false) # hide this part of the scene
```
