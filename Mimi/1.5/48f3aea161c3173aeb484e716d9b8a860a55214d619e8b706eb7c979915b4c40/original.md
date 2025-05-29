```
is_last(ts::VariableTimestep)
```

Return true or false, true if `ts` is the last timestep to be run.  Note that you may run `next_timestep` on `ts`, as ths final timestep has not been run through yet.
