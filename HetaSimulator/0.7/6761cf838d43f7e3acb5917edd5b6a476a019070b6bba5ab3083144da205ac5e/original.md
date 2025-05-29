```
struct Model{IF,OF,EV,SG,EA, MM} <: AbstractModel
  init_func::IF
  ode_func::OF
  events::EV
  saving_generator::SG
  records_output::AbstractVector{Pair{Symbol,Bool}}
  constants::NamedTuple
  events_active::EA
  mass_matrix::MM
end
```

Structure storing core properties of ODE model. This represent the content of one namespace from a Heta platform.

To get list of model content use methods: constants(model), records(model), switchers(model).

To get the default model options use methods:  `events_active(model)`, `events_save(model)`, `observables(model)`. These values can be rewritten by a [`Scenario`]{@ref}.
