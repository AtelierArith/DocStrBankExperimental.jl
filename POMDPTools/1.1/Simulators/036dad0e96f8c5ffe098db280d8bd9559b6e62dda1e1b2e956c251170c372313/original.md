```
sim(polfunc::Function, mdp::MDP; [<keyword arguments>])
sim(polfunc::Function, pomdp::POMDP; [<keyword arguments>])
```

Alternative way of running a simulation with a function specifying how to calculate the action at each timestep.

# Usage

```
sim(mdp) do s
    # code that calculates action `a` based on `s` - this is the policy
    # you can also do other things like display something
    return a
end
```

for an MDP or

```
sim(pomdp) do o
    # code that calculates 'a' based on observation `o`
    # optionally you could save 'o' in a global variable or do a belief update
    return a
end
```

or with a POMDP

```
sim(pomdp, updater) do b
    # code that calculates 'a' based on belief `b`
    # `b` is calculated by `updater`
    return a
end
```

for a POMDP and a belief updater.

# Keyword Arguments

## All Versions

  * `initialstate`: the initial state for the simulation
  * `simulator`: keyword argument to specify any simulator to run the simulation. If nothing is specified for the simulator, a HistoryRecorder will be used as the simulator, with all keyword arguments forwarded to it, e.g.

    ```
    sim(mdp, max_steps=100, show_progress=true) do s
        # ...
    end
    ```

    will limit the simulation to 100 steps.

## POMDP version

  * `initialobs`: this will control the initial observation given to the policy function. If this is not defined, `rand(initialobs(m, s))` will be used if it is available. If it is not, `missing` will be used.

## POMDP and updater version

  * `initialbelief`: `initialize_belief(updater, initialbelief)` is the first belief that will be given to the policy function.
