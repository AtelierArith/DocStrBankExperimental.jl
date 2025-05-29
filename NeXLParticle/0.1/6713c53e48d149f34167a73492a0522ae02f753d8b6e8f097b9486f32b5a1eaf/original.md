```
rca(img::AbstractArray, search::Function, measure::Function, nchords = 16)
rca(blob::Vector{Blob})
```

Search an image for pixels that meet the `search` threshold.  Then using the the rotation chord algorithm find the approximate center of the particle and draw 2 `nchords` at equally spaced angles from the center until the `measure` threshold is no longer met.  The resulting set of perimeter points is stored as a `Vector{CartesianIndex}`.  It is possible that many regios will meet the `search` threshold so the actual result is a `Vector{Vector{CartesianIndex}}`.

Note: The measure `threshold` should be more permissive than the `search` threshold.

Example

```
rca(img, p->p>0.9, p->p>0.7) #
bs = blob(img, p->p>0.7)
rca(bs[1])
```
