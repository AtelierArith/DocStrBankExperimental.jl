```
Problem{S <: IntervalMarkovProcess, F <: Specification}
```

A problem is a tuple of an interval Markov process and a specification.

### Fields

  * `system::S`: interval Markov process.
  * `spec::F`: specification (either temporal logic or reachability-like).
