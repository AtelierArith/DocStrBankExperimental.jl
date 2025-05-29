```
Atom(; <keyword arguments>)
```

An atom and its associated information.

Properties unused in the simulation or in analysis can be left with their default values. The types used should be bits types if the GPU is going to be used.

# Arguments

  * `index::Int`: the index of the atom in the system.
  * `atom_type::T`: the type of the atom.
  * `mass::M=1.0u"g/mol"`: the mass of the atom.
  * `charge::C=0.0`: the charge of the atom, used for electrostatic interactions.
  * `σ::S=0.0u"nm"`: the Lennard-Jones finite distance at which the inter-particle   potential is zero.
  * `ϵ::E=0.0u"kJ * mol^-1"`: the Lennard-Jones depth of the potential well.
