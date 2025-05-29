GR4J Node

GR4J: modèle du Génie Rural à 4 paramètres Journalier.

A four-parameter model with two stores.

# Parameters

  * `x1` : maximum capacity of the production store (mm) (> 0)
  * `x2` : groundwater exchange coefficient (mm) (value < and > 0 possible)
  * `x3` : one day ahead maximum capacity of the routing store (mm, > 0)
  * `x4` : time base of unit hydrograph UH1 (days, > 0.5)

# References

1. Perrin, C., Michel, C., Andréassian, V., 2003.  Improvement of a parsimonious model for streamflow simulation.  Journal of Hydrology 279, 275-289.  https://doi.org/10.1016/S0022-1694(03)00225-7
2. MacDonald, A. 2014.  Python GR4J  https://github.com/amacd31/gr4j
