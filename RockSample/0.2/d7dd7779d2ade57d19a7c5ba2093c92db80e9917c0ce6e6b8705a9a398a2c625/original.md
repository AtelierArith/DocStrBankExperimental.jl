```
RSState{K}
```

Represents the state in a RockSamplePOMDP problem.  `K` is an integer representing the number of rocks

# Fields

  * `pos::RPos` position of the robot
  * `rocks::SVector{K, Bool}` the status of the rocks (false=bad, true=good)
