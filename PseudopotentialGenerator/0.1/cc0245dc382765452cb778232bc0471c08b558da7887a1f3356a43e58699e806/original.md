```
pseudolize(ϕ, ε, vae, mesh, rc; method=:TM)
```

Pseudolize on the pseudo configurations. Loop over the orbitals and do the pseudolization. The function also manage to unscreened the pseudo potential and convert it to the Kleinman-Bylander form.

Methods supported:     - `:TM`: Troullier-Martins pseudopotential     - `:TM22`: (TODO) Troullier-Martins pseudopotential with 22 coefficients (doi:10.1088/1361-648X/aac85d)     - `:RRKJ`: (TODO) Rappe-Rabe-Kaxiras-Joannopoulos pseudopotential (https://doi.org/10.1103/PhysRevB.41.1227)     - `:BHS`: (TODO) Bachelet-Hamann-Schlüter pseudopotential (doi:10.1103/PhysRevB.26.4199)     - more...
