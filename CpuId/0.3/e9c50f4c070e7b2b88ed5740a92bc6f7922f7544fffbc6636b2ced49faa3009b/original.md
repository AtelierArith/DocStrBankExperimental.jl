```
cpucycle()
```

Read the CPU's [Time Stamp Counter, TSC](https://en.wikipedia.org/wiki/Time_Stamp_Counter), directly with a `rdtsc` instruction.  This counter is increased for every CPU cycle, until reset.  This function has, when inlined, practically no overhead and is, thus, probably the fasted method to count how many cycles the CPU has spent working since last read.

Note, the TSC runs at a constant rate if `hasfeature(:TSCINV)==true`; otherwise, it is tied to the current CPU clock frequency.

Hint: This function is extremely efficient when inlined into your own code.       Convince yourself by typing `@code_native CpuId.cpucycle()`.       To use this for benchmarking, simply subtract the results of two calls.       The result is the actual CPU clock cycles spent, independent of the       current (and possible non-constant) CPU clock frequency.
