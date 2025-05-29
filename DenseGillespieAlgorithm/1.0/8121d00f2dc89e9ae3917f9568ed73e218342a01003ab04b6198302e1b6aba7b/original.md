```
    run_gillespie!(time,n₀,par,execute!,rates!,initrates,population_history[,hstart=0,statistic!])
```

Run a exact stochastic simulation, return and fill the `population_history`.

# Arguments

  * `time::AbstracVector`: time interval for the simulation
  * `n₀`: initial population state
  * `par`: additional parameter (gets passed to `execute!` and `rates!`)
  * `execute!`: execute function
  * `rates!`: rates function
  * `initrates`: initial rates
  * `population_history`: empty population history
  * `hstart=0`: time shift for parameter change *(opitonal)*
  * `statistic!`: additional statistic function *(optional)*

# Extended help

  * Note that `n₀,initrates,population_history` all three get modified during the simulation.
  * The algorithm expects the `execute!` function to have the following signature   `julia   execute!(i::Number,n₀,par)`   where the `i` is the event that gets executed and the population state `n₀` gets modified accordingly.   The only exception is when the `initrates` are given as a dictionary. In that case the signature is `execute!(i,trait,n₀,initrates,par)`, where 'trait'   is the key that is modified.
  * The algorithm expects the `rates!` function to have the following signature   `julia   rates!(initrates,n₀,par)`   where the rates get modified according to the current population state given in `n₀`.
  * The algorithm expects the `statistic!` function to have the following signature   `julia   statistic!(population_hist,t,n₀,par)`   where the population history gets modified at position `t` with the current population state `n₀`.
  * Note that the `population_history` needs to be accessible via index from 1 to `length(time)`, or if `hstart` is given from `1+hstart` to `length(time)+hstart`. Unless a specified `statistic!` function is given.
  * Note that the initial population state `n₀` must match the `population_history` in the sense that `population_history :: Vector{typeof(n₀)}`.  Unless a specified `statistic!` function is given.
  * The parameter variable `par` is passed through all functions (`execute!,rates!,statistics!`), thereby affording the user additional flexibility.
