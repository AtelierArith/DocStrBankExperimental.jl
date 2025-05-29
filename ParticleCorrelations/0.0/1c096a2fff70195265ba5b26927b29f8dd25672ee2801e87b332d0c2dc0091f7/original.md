structure*factor(particle*centres::Vector, distances::AbstractVector)

Calculates the isotropic structure_factor from one configuration of particles. To use many configurations of particles, call this function for each, then take the average of the pair-correlation.
