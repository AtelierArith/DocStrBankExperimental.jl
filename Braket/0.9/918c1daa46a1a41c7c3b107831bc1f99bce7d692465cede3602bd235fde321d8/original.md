```
state(j::LocalQuantumJob, ::Val{true})
state(j::LocalQuantumJob, ::Val{false})
state(j::LocalQuantumJob)
```

Fetch the state for job `j`. Local jobs block until they complete, the `state` is always `"COMPLETED"`.
