```
Prometheus.Family{C}(name, help, args..., label_names; registry=DEFAULT_REGISTRY, kwargs...)
```

Create a labeled collector family with labels given by `label_names`. For every new set of label values encountered a new collector of type `C <: Collector` will be created, see [`Prometheus.labels`](@ref).

**Arguments**

  * `name :: String`: the name of the family metric.
  * `help :: String`: the documentation for the family metric.
  * `args...`: any extra positional arguments required for `C`s constructor, see [`Prometheus.labels`](@ref).
  * `label_names`: the label names for the family. Label names can be given as either of the following (typically matching the methods label values will be given later, see [`Prometheus.labels`](@ref)):

      * a tuple of symbols or strings, e.g. `(:target, :status_code)` or `("target", "status_code")`
      * a named tuple type, e.g. `@NamedTuple{target::String, status_code::Int}` where the names are used as the label names
      * a custom struct type, e.g. `RequestLabels` defined as

        ```julia
        struct RequestLabels
            target::String
            status_code::Int
        end
        ```

        where the field names are used for the label names.

**Keyword arguments**

  * `registry :: Prometheus.CollectorRegistry`: the registry in which to register the collector. If not specified the default registry is used. Pass `registry = nothing` to skip registration.
  * `kwargs...`: any extra keyword arguments required for `C`s constructor, see [`Prometheus.labels`](@ref).

**Methods**

  * [`Prometheus.labels`](@ref): get or create the collector for a specific set of labels.
  * [`Prometheus.remove`](@ref): remove the collector for a specific set of labels.
  * [`Prometheus.clear`](@ref): remove all collectors in the family.

# Examples

```julia
# Construct a family of Counters
counter_family = Prometheus.Family{Counter}(
    "http_requests", "Number of HTTP requests", (:target, :status_code),
)

# Increment the counter for the labels `target="/api"` and `status_code=200`
Prometheus.inc(Prometheus.labels(counter_family, (target="/api", status_code=200)))
```
