```
@mt_out_of_order begin expr... end
```

Runs all top-level expressions in `begin expr... end` on parallel multi-threaded tasks.

Example:

``` @mt*out*of_order begin     a = foo()     bar()     c = baz() end

will run `a = foo()`, `bar()` and `c = baz()` in parallel and in arbitrary order, results of assignments will appear in the outside scope.
