```
get_devices(; kwargs...) -> Vector{AwsDevice}
```

Return all AWS Devices satisfying the filters in `kwargs`. The devices have their properties populated and a region-appropriate `AWSConfig` attached.

Valid `kwargs` are:

  * `arns::Vector{String}`: ARNs of devices to search for.
  * `names::Vector{String}`: Names of devices to search for.
  * `types::Vector{String}`: Types of devices (e.g. QPU or simulator) to search for.
  * `statuses::Vector{String}`: Statuses of devices (e.g. `"ONLINE"` or `"OFFLINE"`) to search for.
  * `provider_names::Vector{String}`: Providers of devices to search for.
  * `order_by::String`: property used to sort the devices. Default is `"name"`.
