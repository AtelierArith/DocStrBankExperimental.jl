```
x_points(g::GEQDSKFile)
```

Given a flux map within a GEQDSKFile structure, find X-points. Return a list of X-point R coordinates, Z coordinates, normalized psi values, and a list of flags indicating to which separatrix (primary=1, secondary=2, other=4) they are attached. Separatrix values other than 1, 2, or 4 indicate confusion.

Default settings hopefully work without adjustment, but if you need to fine tune:

neighborhood: number of mesh cells in either direction to include in considering     a local neighborhood; this is for collapsing zones of low bpol into individual     search regions centered on the local minimum of each region. bpol*thresh*factor:     One X-point clearly must be near the global minimum of bpol. But because of     limited grid resolution, the local minimum of bpol near the next X-point     will be larger than the global minimum. Some tolerance is needed to allow     for searching near other low values of bpol. psin*tolerance:     Tolerance in psin for finding the X-point on the primary separatrix (should     nominally have psin=1.0 exactly, by definition, but even with upsampling,     grid resolution isn't infinite).     Also for determining whether additional X-points are on the secondary     separatrix after it is identified. within*limiter_only:     Only look for X-points that are within the limiting surface
