```
shutdown(node)
```

Try to shutdown a process or a supervisor.

If `node` is a supervisor it first attempts to shutdown all children nodes and then it stop the supervisor. If some process refuse to shutdown the `node` supervisor is not stopped.
