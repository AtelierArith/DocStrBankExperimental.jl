Parameterising the way a routing-optimisation problem must be solved. Seven parameters must be chosen (independently of each other):

  * an edge-wise objective function, which assigns a value for each edge, of type `EdgeWiseObjectiveFunction`
  * an aggregation technique to build the complete objective function from the edge-wise pieces, of type `AggregationObjectiveFunction`
  * a formulation type, of type `FormulationType` (for path-based formulations, column generation can be separately enabled)
  * whether column generation is enabled, only for path-based formulations
  * a way to heandle the uncertainty, of type `UncertaintyHandling`
  * a precise algorithm to solve the instance, of type `AlgorithmChoice`
  * a definition of which parameters can be afflicted by uncertainty, of type `UncertainParameters`

The exact algorithm used to solve the instance is based on those seven parameters.
