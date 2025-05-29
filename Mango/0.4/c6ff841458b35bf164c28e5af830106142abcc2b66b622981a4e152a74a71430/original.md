```
activate(runnable, container_list)
```

Actvate the container(s), which includes starting the containers and shutting them down after the runnable has been executed. 

In most cases the runnable will execute code, which starts some process  (e.g. some distributed negotiation) in the system to define the objective of the agent system.

Generally this function is a convenience function and is equivalent to starting all containers  in the list, executing the code represented by `runnable` and shuting down the container again. Further, this function will handle errors occuring while running the `runnable` and ensure the containers are shutting down.

# Examples

```julia
activate(your_containers) do 
   # Send the first message to start the system
   send_message(defined_agent, "Starting somethin", address(other_defined_agent))

   # wait some time
   wait(some_stopping_condition)
end
```
