```
randompointarray(w, h, d; attempts=20)
```

Return an array of randomly positioned points inside the rectangle defined by the current origin (0/0) and the `width` and `height`. `d` determines the minimum distance between each point. Increase `attempts` if you want the function to try harder to fill empty spaces; decrease it if it's taking too long to look for samples that work.

This uses Bridson's Poisson Disk Sampling algorithm: https://www.cs.ubc.ca/~rbridson/docs/bridson-siggraph07-poissondisk.pdf

## Example

```julia
for pt in randompointarray(BoundingBox(), 20)
    randomhue()
    circle(pt, 10, :fill)
end
```
