```
XPRS_SLEEPONTHREADWAIT
```

**Deprecated**In previous versions this was used to determine if the threads should be put into a wait state when waiting for work. (integer)

Default value: `-1`

Values: -1 : Automatically determined depending on the CPU the Optimizer is running on. 0 : Keep the threads busy when waiting for work. 1 : Put the threads into a wait state when waiting for work.
