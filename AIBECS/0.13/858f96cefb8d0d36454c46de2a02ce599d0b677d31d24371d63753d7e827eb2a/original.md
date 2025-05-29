```
PFDO(grd, δz, w_top, w_bot, frac_seafloor, cumfrac_seafloor, fsedremin, Iabove)
```

Returns the particle-flux-divergence operator for a given sinking speed as a function of depth.

This is a slightly different construction where I take in top and bottom settling velocities, and where the bottom one can be modified to further allow a fraction of particles to sink through (buried into) the sea floor.

Below is a detailed explanation of how this function computes the particle-flux divergence. Take these 3 boxes on top of each other:

```
┌──────────────────┐
│ water            │
│←----c----→       │
├───────────┲━━━━━━┥ ←- Φ_top
│           ┃⣿⣿⣿⣿⣿⣿│
│           ┃⣿⣿⣿⣿⣿⣿│
│←-d-→ ←-a-→┃⣿⣿⣿⣿⣿⣿│
├─────┲━━━━━┹──────┤ ←- Φ_bot
│     ┃←----b-----→│
│     ┃⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿│
│     ┃⣿⣿⣿ land ⣿⣿⣿│
│     ┃⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿│
└━━━━━┹────────────┘
```

A part of each of these boxes is water, while the rest is land. For the middle box, we will use the fractional area `a = frac_seafloor` of seafloor, and the cumulated fractional area `b = cumfrac_seafloor` of seafloor, to determine the flux of particles at the top `ϕ_top` and bottom `ϕ_bot`.

From the top box, only the particles in the water can enter the middle box. So the flux at the top of the middle box, `ϕ_top`, is proportional to `c = 1 - Iabove * b`. At the bottom of the middle box, we have to take care of the case of particles hitting the sediments and potentially buried there, or kept in the water. For the part going through the area `d`, the flux is proportional to `d = 1 - b`. For the part going through `a` (hitting the sediments), the flux is proportional to `a * (1 - f)` where `f` is the fraction of particles forcibly kept in the water. (So if `f = 0`, the particles appear to move out of the middle box, but are not carried into the bottom one, and thus are removed from the system / buried.)
