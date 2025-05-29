```
search_devices(; kwargs...) -> Vector{Dict{String, Any}}
```

Search all AWS managed devices and filter the results using `kwargs`.

Valid `kwargs` are:

  * `arns::Vector{String}`: ARNs of devices to search for.
  * `names::Vector{String}`: Names of devices to search for.
  * `types::Vector{String}`: Types of devices (e.g. QPU or simulator) to search for.
  * `statuses::Vector{String}`: Statuses of devices (e.g. `"ONLINE"` or `"OFFLINE"`) to search for.
  * `provider_names::Vector{String}`: Providers of devices to search for.
