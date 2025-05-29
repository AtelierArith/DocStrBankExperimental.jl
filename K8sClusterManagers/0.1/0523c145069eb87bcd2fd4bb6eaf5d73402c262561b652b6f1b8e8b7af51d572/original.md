```
K8sClusterManager(np::Integer; kwargs...)
```

A cluster manager using Kubernetes (k8s) which spawns additional pods as workers. Attempts to spawn `np` workers but may launch with less workers if the cluster has less resources available.

## Arguments

  * `np`: Desired number of worker pods to be launched.

## Keywords

  * `namespace`: the Kubernetes namespace to launch worker pods within. Defaults to `current_namespace()`.
  * `manager_pod_name`: the name of the manager pod. Defaults to `gethostname()` which is the name of the pod when executed inside of a Kubernetes pod.
  * `worker_prefix`: the prefix given to spawned workers. Defaults to `"$(manager_pod_name)-worker"` when the manager is running inside of K8s otherwise defaults to `"witch-worker`.
  * `image`: Docker image to use for the workers. Defaults to the image used by the manager when running inside of a K8s pod otherwise defaults to "julia::VERSION".
  * `cpu`: [CPU resources requested](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#meaning-of-cpu) for each worker. Defaults to `1`,
  * `memory`: [Memory resource requested](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#meaning-of-memory) for each worker in bytes. Requests may provide a unit suffix (e.g. "G" for Gigabytes and "Gi" for Gibibytes). Defaults to `"4Gi"`.
  * `pending_timeout`: The maximum number of seconds to wait for a "Pending" worker pod to enter the "Running" phase. Once the timeout has been reached the manager will continue with the number of workers available (`<= np`). Defaults to `180` (3 minutes).
  * `configure`: A function which allows modification of the worker pod specification before their creation. Defaults to `identity`.
