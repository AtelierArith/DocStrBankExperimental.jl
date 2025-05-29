A simulator that records the history for later examination

The simulation will be terminated when either

1. a terminal state is reached (as determined by `isterminal()` or
2. the discount factor is as small as `eps` or
3. max_steps have been executed

Keyword Arguments:     - `rng`: The random number generator for the simulation     - `capture_exception::Bool`: whether to capture an exception and store it in the history, or let it go uncaught, potentially killing the script     - `show_progress::Bool`: show a progress bar for the simulation     - `eps`     - `max_steps`

Usage (optional arguments in brackets):

```
hr = HistoryRecorder()
history = simulate(hr, pomdp, policy, [updater [, init_belief [, init_state]]])
```
