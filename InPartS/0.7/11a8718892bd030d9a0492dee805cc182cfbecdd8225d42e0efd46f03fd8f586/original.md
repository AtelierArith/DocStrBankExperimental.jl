```
rmparticle!(sim, id) → id
```

Marks the particle with ID `id` for deletion.

## Extended help

Particle IDs marked for deletion are added to a temporary buffer. Deletions are automatically committed by [`evolve!`](@ref) after every timestep. To manually commit the deletions,  use [`flushdeletions!`](@ref).

!!! warning
    Committing the deletions manually is not recommended and may cause the simulation to enter an invalid state!

