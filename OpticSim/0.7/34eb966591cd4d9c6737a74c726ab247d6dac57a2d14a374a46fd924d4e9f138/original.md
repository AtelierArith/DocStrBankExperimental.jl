```
FresnelLens(insidematerial, frontvertex, radius, thickness, semidiameter, groovedepth; conic = 0.0, aspherics = nothing, outsidematerial = AGFFileReader.Air)
```

Create a Fresnel lens as a CSG object, can be concave or convex. Groove positions are found iteratively based on `groovedepth`. For negative radii the vertex on the central surface is at `frontvertex`, so the total thickness of the lens is `thickness` + `groovedepth`. **Aspherics currently not supported**.
