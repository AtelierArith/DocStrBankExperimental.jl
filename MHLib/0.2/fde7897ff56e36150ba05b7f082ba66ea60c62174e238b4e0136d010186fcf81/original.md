```
perform_method!(scheduler, method, solution; delayed_success=false)::Result
```

Perform method on given solution and return `Results` object.

Also updates incumbent, iteration and the method's statistics in method*stats. Furthermore checks the termination condition and eventually sets terminate in the returned Results object. If `delayed*success`, the success is not immediately determined and the statistics updated accordingly but at some later call of`delayed*success*update`.
