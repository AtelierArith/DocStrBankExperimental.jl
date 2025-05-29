```
CutOut2d(bd::BodyDyn,bgs::Vector{BodyGrid})
```

This function need to be called only once after GenerateBodyGrid for 2d case of flat plates(1d body in x-y space).

In `Dyn3d`, bodies are constructed by quadrilateral/triangles(not lines) in z-x plane for both 2d/3d cases. In `ViscousFlow`, fluid in 2d cases are constructed in x-y plane. Thus to describe plates as lines in x-y space, we cut out the info on the other 3 sides of the plate. Note that verts are formulated in clockwise direction, with the left-bottom corner as origin.

If 2d body in x-y plane is constructed in `ViscousFlow`, this function doesn't need to be called.
