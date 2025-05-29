```
abstract type FlowFields
```

Data structure that provide access to flow fields (gridded as arrays) which will be  used to interpolate velocities to individual locations later on (once embedded in an `Individuals` struct). 

Following the C-grid convention also used in `MITgcm` (https://mitgcm.readthedocs.io)  flow fields are expected to be staggered as follows: grid cell i,j has its center located at i-1/2,j-1/2 while the corresponding `u[i,j]` (resp. `v[i,j]) is located at i-1,j-1/2 (resp. i-1/2,j-1). 

Also by convention, velocity fields are expected to have been normalized to grid units (e.g. 1/s rather than m/s) before sending them to one of the supported `FlowFields` constructors (using either `Array` or `MeshArray`):

```
uvArrays(u0,u1,v0,v1,T)
uvwArrays(u0,u1,v0,v1,w0,w1,T)
uvMeshArrays(u0,u1,v0,v1,T,update_location!)
uvwMeshArrays(u0,u1,v0,v1,w0,w1,T,update_location!)
```

Using the `FlowFields` constructor which gets selected by the type of `u0` etc. For example :

```
F=FlowFields(u,u,v,v,0*w,1*w,[0.0,10.0])
F=FlowFields(u,u,v,v,[0.0,10.0],func)
```

as shown in the online documentation examples.
