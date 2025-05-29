```
spawnbg(f)
```

Spawn work on any available background thread. Captures any exception thrown in the thread, to give better stacktraces.

You can use `checked_fetch(spawnbg(f))` to rethrow any exception.

```
** Warning ** this doesn't compose with other ways of scheduling threads
So, one should use `spawn_background` exclusively in each Julia process.
```
