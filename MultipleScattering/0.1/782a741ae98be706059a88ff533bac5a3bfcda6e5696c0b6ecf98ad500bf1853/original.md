```
random_particles(particle_medium, particle_shapes::Vector{Shape}, region_shape, volume_fraction::Number;
    seed=Random.make_seed())
random_particles(particle_medium, particle_shape::Shape, region_shape, volume_fraction::Number;
    seed=Random.make_seed())
random_particles(particle_medium, particle_shape::Shape, region_shape, N::Integer;
    seed=Random.make_seed())
```

Generate `N` random particles that fit inside `region_shape` (or fill with `volume_fraction`)

Specify seed to make output deterministic. Algorithm places particles unifomly randomly inside the bounding box of `region_shape` and discards particle if it overlaps (based on outer radius) or does not lies completely in box.

When passing particle_shapes::Vector{Shape} we assume each element is equally likely to occur. Repeating the same shape will lead to it being placed more often.
