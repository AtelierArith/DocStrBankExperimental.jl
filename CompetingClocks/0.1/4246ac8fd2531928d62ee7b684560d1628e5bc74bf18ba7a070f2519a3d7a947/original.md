```
DebugWatcher()
```

For debugging, it helps to have visibility into the simulation. This Watcher records everything that is enabled or disabled as a list of all enables and all disabled. It's the complete event history, and you can think of it as the filtration for the process going forward.

```
watcher = DebugWatcher{String}()
# enable and disable some things.
(watcher.enabled[1].clock,
watcher.enabled[1].distribution,
watcher.enabled[1].te,
watcher.enabled[1].when)
```
