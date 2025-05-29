```
ThreadsEx(;scheduler::Symbol = :dynamic)
```

Uses Julia's Threads @threads macro when computing the intensitymap or visibilitymap. You can choose from Julia's various schedulers by passing the scheduler as a parameter. The default is :dynamic, but it isn't considered part of the stable API and may change at any moment.
