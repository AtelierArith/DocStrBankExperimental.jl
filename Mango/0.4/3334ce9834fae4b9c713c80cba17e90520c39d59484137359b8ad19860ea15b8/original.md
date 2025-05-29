```
run_in_real_time(runnable::Function,
n_container::Int,
container_list_creator::Function,
agents::Agent...)
```

Let the agents run in containers (real time).

Distributes the given `agents` contained in the agent*tuple to `n*container`(real time container) and execute the`runnable`  (takes the container list as argument) while the container are active to run. 
