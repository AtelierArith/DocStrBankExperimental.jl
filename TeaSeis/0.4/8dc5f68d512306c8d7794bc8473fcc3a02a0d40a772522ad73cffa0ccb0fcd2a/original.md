```
g = Geometry(;ox=0.0,oy=0.0,oz=0.0,ux=1.0,uy=0.0,uz=0.0,vx=0.0,vy=1.0,vz=0.0,wx=0.0,wy=0.0,wz=1.0,u1=0,un=0,v1=0,vn=0,w1=0,wn=0)
```

where `g::Geometry`.  The named arguments are:

  * `ox=0.0,oy=0.0,oz=0.0` origin of axes
  * `ux=1.0,uy=0.0,uz=0.0` end of u-vector (e.g. end of first in-line, in the cross-line direction
  * `vx=0.0,vy=1.0,vz=0.0` end of v-vector (e.g. end of first cross-line, in the in-line direction
  * `wx=0.0,wy=0.0,wz=1.0` end of depth axis
  * `u1=1` minimum index along the u-vector (e.g. maximum cross-line index)
  * `un=2` maximum index along the u-vector (e.g. maximum cross-line index)
  * `v1=1` minimum index along the v-vector (e.g. minimum in-line index)
  * `vn=2` maximum index along the v-vector (e.g. maximum in-line index)
  * `w1=1` minimum depth index
  * `wn=2` maximum depth index
