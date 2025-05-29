```
Workflow(jobs::AbstractJob...)
```

Create a `Workflow` from a given series of `AbstractJob`s.

The list of `AbstractJob`s does not have to be complete, our algorithm will find all connected `AbstractJob`s automatically.
