```
cputhreads()
```

Determine the number of logical cores on the current executing CPU by invoking a `cpuid` instruction.  On systems with multiple CPUs, this only gives information on the single CPU that is executing the code. Returns zero if querying this feature is not supported, which may also be due to a running hypervisor (as observed on hvvendor() == :Microsoft).

In contrast to `cpucores()`, this function also takes logical cores aka hyperthreading into account.  For practical purposes, only I/O intensive code should make use of these total number of cores; memory or computation bound code will not benefit, but rather experience a detrimental effect.

See also Julia's global variable `Base.Sys.CPU_THREADS`, which gives the total count of all logical cores on the machine.  Thus, `Base.Sys.CPU_THREADS ÷ CpuId.cputhreads()` should give you the number of CPUs (packages) in your system.
