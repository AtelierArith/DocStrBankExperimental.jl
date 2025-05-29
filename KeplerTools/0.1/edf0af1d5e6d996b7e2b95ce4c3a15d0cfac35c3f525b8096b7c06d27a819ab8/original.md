```
Δθ = angle_in_plane(vec, mat)
Δθ = angle_in_plane(vec1, vec2, mat)
Δθ = angle_in_plane(vec, orbit)
Δθ = angle_in_plane(vec, vec, orbit)
Δθ = angle_in_plane(vec, orbit, t)
Δθ = angle_in_plane(orbit1, orbit2, t)
```

Computes the angle between two vectors after projecting them to the orbital plane defined by an orbit's basis matrix `mat`. 

If only one vector is provided, the angle between the vector `vec` and the orbit's periapsis is found. 

If a vector, orbit, and time `t` are provided, the in-plane angle between the vector and the orbit's  position at `t` is found.

If two orbits and a time `t` are provide, the in-plane angle between the two orbits' positions at time `t` is found.
