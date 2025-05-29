```
run_with_tcp(runnable::Function,
n_container::Int,
agent_tuples::Union{Tuple,Agent}...;
host::String="127.0.0.1",
start_port::Int=5555,
codec::Union{Nothing,Tuple{Function,Function}}=(encode, decode))
```

Let the agents run in tcp containers (real time).

Distributes the given `agent_tuples` to `n_container` (real time container) and execute the `runnable`  (takes the container list as argument) while the container are active to run. It is possible to  add supplementary information per agent as Tuple. For example `(Agent, :aid => "my_aid")`. Here, TCP container are created on `host` starting with the port `start_port`.
