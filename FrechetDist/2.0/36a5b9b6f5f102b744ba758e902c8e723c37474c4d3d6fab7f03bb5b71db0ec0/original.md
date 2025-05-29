```
frechet_d_compute_sample
```

Computes the discrete Frechet distance between the two curves.by sampling them

It first sapmles the two curves rougly uniformly. n is supposed to be the nubmer of vertices, by the optput might be a sample that is slightly bigger, as the code tries to ensure the vertices are being picked.

# Arguments

  * `n`: number of vertices to add when "refining" the two curves. The number of vertices computed might be larger (but hopefully not much larger).
  * f_lopt    true: Use the rectractable Frechet distance version    false: Use the standard discrete Frechet version.
