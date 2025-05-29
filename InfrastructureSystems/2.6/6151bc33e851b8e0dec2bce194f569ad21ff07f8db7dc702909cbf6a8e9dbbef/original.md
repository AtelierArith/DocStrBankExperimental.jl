Given some [`ComponentContainer`](@ref)-like source of components to draw from, such as a [`PowerSystems.System`](@extref), a `ComponentSelector` picks out a certain subset of them based on some user-defined selection criteria. A `ComponentSelector` can also be used to name that subset of components or to split it up into groups. The same `ComponentSelector` can be used to apply the same set of selection criteria to multiple sources of components. The primary use case for `ComponentSelector` is to support repeatable multi-scenario post-processing analytics (see e.g. [`PowerAnalytics.jl`](https://nrel-sienna.github.io/PowerAnalytics.jl/stable/)).

Formally, instances of `ComponentSelector` represent lazy, partitioned, named, source-independent collections of [`InfrastructureSystemsComponent`](@ref)s.

# Core Interface

  * [`make_selector`](@ref): factory function to handle `ComponentSelector` creation; end users should use this rather than calling the constructors directly.
  * `get_groups`: get the groups that make up a `ComponentSelector`, which will themselves be represented as `ComponentSelector`s.
  * `get_components`: get all the components that make up a `ComponentSelector`, ignoring how they are grouped. A component should appear in the `get_components` of a given selector if and only if it appears in the `get_components` of at least one of that selector's groups.
  * [`get_name`](@ref): get the name of the `ComponentSelector`. All `ComponentSelector`s have a name, whether it is specified by the user or created automatically.
  * [`rebuild_selector`](@ref): create a new `ComponentSelector` from an existing one with some details (e.g., the name or the grouping behavior) tweaked.

# Availability Filtering

Besides the core interface, also provided are `get_component` for `ComponentSelector` subtypes that can only refer to at most one component; and `get_available_component`, `get_available_components`, and `get_available_groups`, which work the same as the corresponding functions without `available` except they only consider components for which `get_available` is true.

# `scope_limiter` Filtering

The `ComponentSelector` methods of `get_component`, `get_components`, and `get_groups`, and the corresponding `_available_` variants, take an optional first argument `scope_limiter::Union{Function, Nothing}`. If a function is passed in here, it will be used as a filter function to limit the components under consideration before the `ComponentSelector`'s criteria are evaluated.
