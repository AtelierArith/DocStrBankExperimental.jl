```
run_in_real_time(runnable::Function,
n_container::Int,
container_list_creator::Function,
agent_tuple::Tuple...)
```

Let the agents run in containers (real time).

Distributes the given agents contained in the `agent_tuple` to `n_container` (real time container) and execute the `runnable`  (takes the container list as argument) while the container are active to run. It is possible to  add supplementary information per agent as Tuple. For example `(Agent, :aid => "my_aid")`. The type of the containers are determined by the `container_list_creator` (n*container as argument, has to return a list of container with n*container entries).
