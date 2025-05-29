```
load_problem(repository, domain, problem)
load_problem(repository, collection, domain, problem)
```

Load a problem (specified as a name or index) from a planning `repository` for a given `domain`. In some repositories, domains are also organized into `collection`s.

The following repositores are currently supported:

  * [`JuliaPlannersRepo`](@ref): Repository maintained by the JuliaPlanners organization
  * [`IPCInstancesRepo`](@ref): International Planning Competition domains and problems
  * [`PlanningDomainsRepo`](@ref): Repository provided by http://planning.domains/

View the documentation of each repository for more information.
