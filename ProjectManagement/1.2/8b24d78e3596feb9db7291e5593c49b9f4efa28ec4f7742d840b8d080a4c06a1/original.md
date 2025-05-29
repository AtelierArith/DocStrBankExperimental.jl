```
Project(task_durations, links)
```

  * `task_durations::NamedTuple`: a namedtuple where the keys are the names of the tasks, and the values indicate the timing.

      * The timing values can be a `Real` value (like 5.0) to represent a fixed duration; or anything sampleable to represent a duration only probabilistically known. i.e. any object `dur` that has `rand(rng, dur)::Real` defined on it. e.g. any collection or distribution object. Particularly relevent is `PertBeta(min, mode, max)` which is the standard used for PERT estimation.
  * `links::Vector{Pair{Symbol, Symbol}}`: a collection of pairs for all the depencencies of tasks. e.g. `[:a => :b, :a=>:c, :c=>:d]`. A convienent way to write this is often using broadcasting and matrix notation for vcat: `[:a .=> [:b, :c]; :c => :d]`.

The task names `start` and `finish` are special, in that they represent the begining and ending milestones of the project. They must be in the `task_durations` with duration `0`, and they respectively must be the root and only leaf of the graph decribed by the `links`.
