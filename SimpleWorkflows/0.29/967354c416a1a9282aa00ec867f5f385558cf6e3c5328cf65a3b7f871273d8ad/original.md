```
isfailed(wf::AbstractWorkflow)
```

Check if any job in the `AbstractWorkflow` has failed, given that all jobs have exited.

Return `true` if any job has failed after all jobs have exited, otherwise, return `false`.
