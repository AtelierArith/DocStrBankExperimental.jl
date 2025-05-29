```
AttractorSeedContinueMatch(mapper, matcher = MatchBySSSetDistance(); seeding)
```

A global continuation method for [`global_continuation`](@ref). `mapper` is any subtype of [`AttractorMapper`](@ref) which implements [`extract_attractors`](@ref), i.e., it finds the actual attractors. `matcher` is a configuration of how to match attractor IDs, see [`IDMatcher`](@ref) for more options.

## Description

This is a general/composable global continuation method based on a 4-step process:

1. Seed initial conditions from previously found attractors
2. Propagate those forwards to "continue" previous attractors
3. Estimate basin fractions and potentially find new attractors
4. Match attractors

### Step 0 - Finding initial attractors

At the first parameter slice of the global continuation process, attractors and their fractions are found using the given `mapper` and [`basins_fractions`](@ref). See the `mapper` documentation and [`AttractorMapper`](@ref) for details on how this works. Then, from the second parameter onwards the continuation occurs.

### Step 1 - Seeding initial conditions

Initial conditions can be seeded from previously found attractors. This is controlled by the `seeding` keyword, which must be a function that given a `StateSpaceSet` (an attractor), it returns an iterator of initial conditions. By default the first point of an attractor is provided as the only seed.

Seeding can be turned off by providing the dummy function `seeding = A -> []`, i.e., it always returns an empty iterator and hence no seeds and we skip to step 2.

### Step 2 - Continuing the seeds

The dynamical system referenced by the `mapper` is now set to the new parameter value. The seeds are run through the `mapper` to converge to attractors at the new parameter value. Seeding initial conditions close to previous attractors increases the probability that if an attractor continues to exist in the new parameter, it is found. Additionally, for some `mappers` this seeding process improves the accuracy as well as performance of finding attractors, see e.g. discussion in [Datseris2023](@cite).

This seeding works for any `mapper`, regardless of if they can map individual initial conditions with the `mapper(u0)` syntax! If this syntax isn't supported, steps 2 and 3 are done together.

### Step 3 - Estimate basins fractions

After the special seeded initial conditions are mapped to attractors, attractor basin fractions are computed by sampling additional initial conditions using the provided `ics` in [`global_continuation`](@ref). I.e., exactly as in [`basins_fractions`](@ref). Naturally, during this step new attractors may be found, besides those found using the "seeding from previous attractors".

### Step 4 - Matching

Normally the ID an attractor gets assigned is somewhat a random integer. Therefore, to ensure a logical output of the global continuation process, attractors need to be "matched". This means: attractor and fractions must have their *IDs changed*, so that attractors that are "similar" to those at a previous parameter get assigned the same ID.

What is "similar enough" is controlled by the `matcher` input. The default `matcher` [`MatchBySSSetDistance`](@ref) matches sets which have small distance in state space. The matching algorithm itself can be quite involved, so read the documentation of the `matcher` for how matching works.

A note on matching: the [`MatchBySSSetDistance`](@ref) can also be used after the continuation is completed, as it only requires as input the state space sets (attractors), without caring at which parameter each attractor exists at. If you don't like the final matching output, you may use a different instance of [`MatchBySSSetDistance`](@ref) and call [`match_sequentially!`](@ref) again on the output, without having to recompute the whole global continuation!

### Step 5 - Finish

After matching the parameter(s) is incremented. Steps 1-4 repeat until all parameter values are exhausted.

### Further note

This global continuation method is a generalization of the "RAFM" continuation described in [Datseris2023](@cite). This continuation method is still exported as [`RecurrencesFindAndMatch`](@ref).
