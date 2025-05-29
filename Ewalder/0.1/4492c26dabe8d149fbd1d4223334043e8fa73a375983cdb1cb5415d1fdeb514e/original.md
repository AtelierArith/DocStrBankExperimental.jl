```
energy(sys::System; charges=Float64[], dipoles=Vec3[])
```

Calculate the Ewald energy in units of $1/4\pi\epsilon_0$ for a periodic system of `charges` and `dipoles`. If either charge or dipole parameters are omitted, they will be assumed zero. A neighbors list can also be optionally provided; see the source code for details.
