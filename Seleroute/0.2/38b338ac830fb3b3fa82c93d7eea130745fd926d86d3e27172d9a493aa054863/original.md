The aggregation-function objective to optimise, giving one objective function aggregating all the components for each edge (indicated by `EdgeWiseObjectiveFunction`). These values are natively supported:

  * `MinimumTotal`: the total considered value is minimised.
  * `MinimumMaximum`: the maximum considered value is minimised.
  * `MinMaxFair`: a min-max-fair solution is computed with respect to the considered value. By definition, this means that each user has their own value; not a single user can reduce this value without others seeing an increase.

In theory, a max-min fair solution is kept when any nondecreasing function is applied on the criteria. It becomes a min-max fair solution if the function is nonincreasing. In practice, it means that using `MinMaxFair` with `KleinrockLoad` or `Load` should give the same solution. The solver will not forbid such combinations, though.
