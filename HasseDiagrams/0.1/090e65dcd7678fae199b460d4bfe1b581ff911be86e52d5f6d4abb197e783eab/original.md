```
force_layout(p::Poset)
```

Compute a poset in which the edges of the cover digraph act like springs and  the nodes act like repelling particles. The y-coordinates are determined by  `layered_layout_2` and then we optimize the x-coordinates. Sometimes gives good images, but can be sluggish. 
