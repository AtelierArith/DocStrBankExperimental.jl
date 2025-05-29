```
load_domain(repository, domain)
load_domain(repository, collection, domain)
```

Load a domain from a planning `repository`. In some repositories, domains are also organized into `collection`s.

The following repositores are currently supported:

  * [`JuliaPlannersRepo`](@ref): Repository maintained by the JuliaPlanners organization
  * [`IPCInstancesRepo`](@ref): International Planning Competition domains and problems
  * [`PlanningDomainsRepo`](@ref): Repository provided by http://planning.domains/

View the documentation of each repository for more information.
