```
MHMethod
```

(Wrapper for) a method (function) to be applied to a solution by the scheduler.

# Elements

  * 'name`: name of the method; must be unique over all used methods
  * `method`: a function called for a Solution object;    the function must have exactly three parameters, which are the solution,       a general parameter of arbitrary type (or `nothing`), and a `Result` structure
  * `par`: a parameter provided when calling the method; can be `nothing`
