```
struct MetricProblem{T <: Vector{IOExample}}
```

Program synthesis problem defined by an specification and a metric. The specification has to be based on input/output examples, while the function needs to return a numerical value.
