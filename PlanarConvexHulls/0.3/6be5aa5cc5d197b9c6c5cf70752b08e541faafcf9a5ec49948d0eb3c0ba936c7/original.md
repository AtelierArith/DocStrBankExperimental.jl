```julia
jarvis_march!(hull, points; atol)

```

Compute the convex hull of `points` and store the result in `hull` using the [Jarvis march (gift wrapping) algorithm](https://en.wikipedia.org/wiki/Gift_wrapping_algorithm). This algorithm has $O(nh)$ complexity, where $n$ is the number of points and $h$ is the number of vertices of the convex hull.
