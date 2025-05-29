```
cpucycle_id()
```

Read the CPU's [Time Stamp Counter, TSC](https://en.wikipedia.org/wiki/Time_Stamp_Counter), and executing CPU id directly with a `rdtscp` instruction.  This function is similar to the `cpucycle()`, but uses an instruction that also allows to detect if the code has been moved to a different executing CPU.  See also the comments for `cpucycle()` which equally apply.
