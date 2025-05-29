```
radial_stub(r, Θ, h, t; narc::Int=197)
```

See also the documentation for `radial_cut`.

Return a polygon for a radial stub. The polygon has to be subtracted from a ground plane, and will leave a defect in the ground plane of uniform width `t` that outlines the (metallic) radial stub. `r` refers to the radius of the actual stub, not the radius of the circular arc bounding the ground plane defect. Likewise `h` has an analogous meaning to that in `radial_cut` except it refers here to the radial stub, not the ground plane defect.
