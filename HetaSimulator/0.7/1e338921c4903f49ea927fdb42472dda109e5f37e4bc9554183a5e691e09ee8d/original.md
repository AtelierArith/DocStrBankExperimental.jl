```
struct Platform{M,C}
  models::Dict{Symbol,M}     # dictionary storing Models
  scenarios::Dict{Symbol,C} # dictionary storing Scenarios
end
```

The main storage representing a modeling platform. Typically HetaSimulator works with one platform object which can include several models and scenarios.

Usually a `Platform` is created based on Heta formatted files using [`load_platform`]{@ref}.

To get the platform content use methods: `models(platform)`, `scenarios(platform).
