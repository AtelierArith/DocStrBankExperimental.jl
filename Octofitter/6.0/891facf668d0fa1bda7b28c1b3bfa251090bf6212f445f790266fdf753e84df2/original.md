```
ObsPriorAstromONeil2019(astrometry_likelihood, period_prior)
```

Given a an astrometry likelihood (`PlanetRelAstromLikelihood`), apply the "observable based priors" of K. O'Neil 2019 "Improving Orbit Estimates for Incomplete Orbits with a New Approach to Priors: with Applications from Black Holes to Planets".

This prior correction is only correct if you supply Uniform priors on  all Campbell orbital parameters and a Uniform prior on Period (not semi-major axis). This period prior has a significant impact in the fit and recommendations for its range were not published in the original paper.

## Examples

```julia
astrom_like = PlanetRelAstromLikelihood(astrom_table)

# Apply observable based priors ontop of our uniform Campbell priors:
obs_prior = ObsPriorAstromONeil2019(astrom_like)

# The astrometry lieklihood object is passed as a first parameter
# since the obserable-based priors depend on the observation 
# epochs.

@planet b Visual{KepOrbit} begin
    # Instead of a prior on sma
    # a ~ Uniform(0.001, 10000)

    # Put a prior on period:
	P ~ Uniform(0.001, 2000) # yrs
    a = cbrt(system.M * b.P^2)

    # Keep sine prior on inclination
    i ~ Sine()

    # Rest are uniform
    e ~ Uniform(0.0, 1.0)
    ω ~ UniformCircular()
    Ω ~ UniformCircular()
    τ ~ UniformCircular(1.0)
end astrom_like obs_prior
```
