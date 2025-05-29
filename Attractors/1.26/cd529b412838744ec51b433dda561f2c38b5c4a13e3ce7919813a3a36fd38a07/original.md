```
MCSBruteForce(; kwargs...)
```

The brute force randomized search algorithm used in [`minimal_critical_shock`](@ref).

It consists of two steps: random initialization and sphere radius reduction. On the first step, the algorithm generates random perturbations within the search area and records the perturbation that leads to a different basin but with the smallest magnitude. With this obtained perturbation it proceeds to the second step. On the second step, the algorithm generates random perturbations on the surface of the hypersphere with radius equal to the norm of the perturbation found in the first step. It reduces the radius of the hypersphere and continues searching for the better result with a smaller radius. Each time a better result is found, the radius is reduced further.

The algorithm records the perturbation with smallest radius that leads to a different basin.

Because this algorithm is based on hyperspheres, it assumes the Euclidean norm as the metric.

## Keyword arguments

  * `initial_iterations = 10000`: number of random perturbations to try in the first step of the algorithm.
  * `sphere_iterations = 10000`: number of steps while initializing random points on hypersphere and decreasing its radius.
  * `sphere_decrease_factor = 0.999`: factor by which the radius of the hypersphere is decreased (at each step the radius is multiplied by this number). Number closer to 1 means more refined accuracy.
  * `seed = rand(1:10000)`: seed for the random number generator used when sampling random perturbations.
