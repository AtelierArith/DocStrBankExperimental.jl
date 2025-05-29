```
run_with_tcp(runnable::Function,
n_container::Int,
agents::Agent...;
host::String="127.0.0.1",
start_port::Int=5555,
codec::Union{Nothing,Tuple{Function,Function}}=(encode, decode))
```

Let the `agents` run in tcp containers (real time).

Distributes the given `agents` to `n_container` (real time container) and execute the `runnable`  (takes the container list as argument) while the container are active to run. Here, TCP container are created on `host` starting with the port `start_port`.
