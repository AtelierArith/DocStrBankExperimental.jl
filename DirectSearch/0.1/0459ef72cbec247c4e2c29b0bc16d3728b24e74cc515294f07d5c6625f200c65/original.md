```
Optimize!(p::DSProblem)
```

Run the direct search algorithm on problem `p`.

`p` must have had its initial point and objective function set. If extreme barrier constraints have been set then the initial point must be value for those constraints.
