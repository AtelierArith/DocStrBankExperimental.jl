```
tick()
```

Start a timer.

Other functions:

  * `tock()` (stop counting and show canonical)
  * `tok()` (stop counting and return seconds)
  * `peektimer()` (continue counting, return elapsed seconds)
  * `laptimer()` (continue counting, show canonical)

If `ENV["TICKTOCK_MESSAGES"]` = `false`, `tick()` will not display messages.
