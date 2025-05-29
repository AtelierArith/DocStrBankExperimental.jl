The type of formulation that is used to solve the routing problem. This package natively supports two main families of formulations:

  * `FlowFormulation`: each edge is explicitly present in the model
  * `PathFormulation`: the model uses path variables. The path-based formulations can be solved in two ways:

      * precomputing paths: only the set of precomputed paths is considered; if not enough paths are precomputed, the solution is only approximate, and no approximation factor is guaranteed
      * column generation: new paths are added on the fly, when they might improve the solution
