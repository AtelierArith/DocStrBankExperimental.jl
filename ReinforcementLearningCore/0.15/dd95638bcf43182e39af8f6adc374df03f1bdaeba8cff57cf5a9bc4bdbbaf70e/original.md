```
Agent(;policy, trajectory) <: AbstractPolicy
```

A wrapper of an `AbstractPolicy`. Generally speaking, it does nothing but to update the trajectory and policy appropriately in different stages. Agent is a Callable and its call method accepts varargs and keyword arguments to be passed to the policy. 
