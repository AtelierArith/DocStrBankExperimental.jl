```
bisect_to_edge(pds::ParallelDynamicalSystem, mapper::AttractorMapper; kwargs...) -> u1, u2
```

Finds the basin boundary between two states `u1, u2 = current_states(pds)` by bisecting along a straight line in phase space. The states `u1` and `u2` must belong to different basins.

Returns a triple `u1, u2, success`, where `u1, u2` are two new states located on either side of the basin boundary that lie less than `bisect_thresh` (Euclidean distance in state space) apart from each other, and `success` is a Bool indicating whether the bisection was successful (it may fail if the `mapper` maps both states to the same basin of attraction, in which case a warning is raised).

## Keyword arguments

  * `bisect_thresh = 1e-7`: The maximum (Euclidean) distance between the two returned states.

## Description

`pds` is a `ParallelDynamicalSystem` with two states. The `mapper` must be an `AttractorMapper` of subtype `AttractorsViaProximity` or `AttractorsViaRecurrences`.

!!! info
    If the straight line between `u1` and `u2` intersects the basin boundary multiple times, the method will find one of these intersection points. If more than two attractors exist, one of the two returned states may belong to a different basin than the initial conditions `u1` and `u2`. A warning is raised if the bisection involves a third basin.

