```
apply!(sim, func, call, read, write; [add_existing, with_edge])
```

Apply the transition function `func` to the simulation state. 

`call` must be a single agent type or a collection of agent types, likewise `read` and `write` must be a single agent/edge type or a collection of agent/edge types.

`call` determines for which agent types the transition function `func` is called. Within the transition function, an agent has access to the state of agents (including its own state) and to edges only if their types are in the `read` collection. Accordingly, the agent can change its own state and/or create new agents or edges only if their types are in the `write` collection.

Assume that T is an agent type that is in `call`. In case T is also in `read`, the transition function must have the following signature: `transition_function(agent::T, id, sim)`, where the type declaration of agent is optional if `call` contains only a single type. If T is not in `read`, it must have the signature `transition_function(::Val{T}, id::AgentID, sim::Simulation)`.

If T is in `write`, the transition function must return either an agent of type T or `nothing`. If `nothing` is returned, the agent will be removed from the simulation, otherwise the agent with id `id` will get the returned state after the transition function was called for all agents.

When an edge state type is in `write`, the current edges of that type are removed from the simulation. If you want to keep the existing edges for a specific type, you can add this type to the optional `add_existing` collection.

Similarly, agent types that are in the `write` but not in the `call` argument can be part of the `add_existing` collection, so that the existing agents of this type are retained and can only be added. For agent types in `call`, however, this is achieved by returning their state in the transition function.

With the keyword `with_edge` it is possible to restrict the set of agents for which the transition function is called to those agents who are on the target side of edges of the type `with_edge`. So  

```
apply!(sim, AT, ET, []) do _, id, sim 
    if has_edge(sim, id, ET)
       do_something
    end
end
```

is equivalent to 

```
apply!(sim, AT, ET, []; with_edge = ET) do _, id, sim 
    do_something
end
```

but saves all the `has_edge` checks.

This `with_edge` keyword should only be set when a small subset of agents possess edges of this particular type, as performance will be adversely impacted in other scenarios. Also the keyword can only be used for edgetypes without the :SingleType hint.

See also [`apply`](@ref) and the [Applying Transition Function section in the tutorial](tutorial1.md#Applying-Transition-Functions)
