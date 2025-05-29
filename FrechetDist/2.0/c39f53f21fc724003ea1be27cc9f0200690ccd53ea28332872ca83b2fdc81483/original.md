```
frechet_width_approx
```

2-approximation to the Frechet distance between    seg = P[first(rng)]-P[last(rng)] and he polygon    P[rng]  Here, rng is a range i:j

This function implements a greedy matching alnog the segment - you move to the cloest point on seg to the current point, making sure never moving back.
