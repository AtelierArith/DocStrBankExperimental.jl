```
info(lk::Link)
```

Return the state of an actor associated with `lk`:

  * `Actors.Info` if it is runnable,
  * `:done` if it has finished,
  * else return the failed task.
