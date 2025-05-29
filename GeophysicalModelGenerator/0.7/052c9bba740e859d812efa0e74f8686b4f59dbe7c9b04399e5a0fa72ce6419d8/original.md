```
d_cart = project_CartData(d_cart::CartData, d::UTMData, p::ProjectionPoint)
```

Projects all datafields from the UTMData struct `d` to the CartData struct `d_cart`, around the projection point `p`.     `d_cart` *must* be an orthogonal cartesian grid (deformed doesn't work; use `convert2CartData(d, proj)`, where `proj` is a projection point in that case).

```
# Note:    
- If `d_cart` and `d` are horizontal surfaces (3rd dimension has size==1), it also interpolates the depth coordinate.
```
