```
cpucores()
```

Determine the number of physical cores on the current executing CPU by invoking a `cpuid` instruction.  On systems with multiple CPUs, this only gives information on the single CPU that is executing the code. Returns zero if querying this feature is not supported, which may also be due to a running hypervisor (as observed on hvvendor() == :Microsoft).

Also, this function does not take logical cores (aka hyperthreading) into account, but determines the true number of physical cores, which typically also share L3 caches and main memory bandwidth.

See also the Julia global variable `Base.Sys.CPU_THREADS`, which gives the total count of all logical cores on the machine.
