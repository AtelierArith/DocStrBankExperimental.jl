```
Resource(;attributes=nothing, schema_url="", default_attributes=OTEL_RESOURCE_ATTRIBUTES())
```

Quoted from [the specification](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/overview.md#resources):

> Resource captures information about the entity for which telemetry is recorded. For example, metrics exposed by a Kubernetes container can be linked to a resource that specifies the cluster, namespace, pod, and container name.
>
> Resource may capture an entire hierarchy of entity identification. It may describe the host in the cloud and specific container or an application running in the process.

