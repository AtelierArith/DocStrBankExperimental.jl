```
simplex(vertices)
simplex(v1, v2, ...)
simplex(vertices, Val{D})
```

Build a D-dimensional simplex. The vertices can be passed in an array (static or dynamic), or supplied separately. If the length of the array is not part of its type, the speed of the construction can be improved by supplying an extra Val{D} argument. In case it is not clear from the context whether the vertex array is dynamically or statically sized, use the third form as it will not incur notable performance hits.

Note that D is the dimension of the simplex, i.e. the number of vertices supplied minus one.
