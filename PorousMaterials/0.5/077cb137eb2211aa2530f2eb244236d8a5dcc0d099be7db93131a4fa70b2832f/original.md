```
energy = lennard_jones(r², σ², ϵ)  (units: Kelvin)
```

Calculate the lennard jones potential energy given the square of the radius r between two lennard-jones spheres. σ and ϵ are specific to interaction between two elements. Return the potential energy in units Kelvin (well, whatever the units of ϵ are).

# Arguments

  * `r²::Float64`: distance between two (pseudo)atoms in question squared (Angstrom²)
  * `σ²::Float64`: sigma parameter in Lennard Jones potential squared (units: Angstrom²)
  * `ϵ::Float64`: epsilon parameter in Lennard Jones potential (units: Kelvin)

# Returns

  * `energy::Float64`: Lennard Jones potential energy
