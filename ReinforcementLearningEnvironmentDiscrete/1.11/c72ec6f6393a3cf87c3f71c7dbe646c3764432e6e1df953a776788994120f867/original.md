```
DiscreteMaze(; nx = 40, ny = 40, nwalls = div(nx*ny, 10), ngoals = 1,
               goalrewards = 1, stepcost = 0, stochastic = false, 
               neighbourstateweight = .05)
```

Returns a `DiscreteMaze` of width `nx` and height `ny` with `nwalls` walls and `ngoals` goal locations with reward `goalreward` (a list of different rewards for the different goal states or constant reward for all goals), cost of moving  `stepcost` (reward = -`stepcost`); if `stochastic = true` the actions lead with a certain probability to a neighbouring state, where `neighbourstateweight` controls this probability.
