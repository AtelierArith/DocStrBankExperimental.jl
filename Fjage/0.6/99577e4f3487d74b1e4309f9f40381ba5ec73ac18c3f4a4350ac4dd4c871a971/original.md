```
shutdown(a::Agent)
```

This function is called when an agent terminates. An agent may provide a method to handle termination, if desired.

# Examples:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.shutdown(a::MyAgent)
  @info "MyAgent shutting down"
end
```
