```
abstract type Solver
```

Abstract constraint solver.  Each solver should have at least the following fields:

  * `statistics::TimerOutput`
  * `fix_point_running::Bool`
  * `schedule::PriorityQueue{AbstractLocalConstraint, Int}`

Each solver should implement at least:

  * `post!`
  * `get_tree`
  * `get_grammar`
  * `set_infeasible!`
  * `isfeasible`
  * `HerbCore.get_node_at_location`
  * `get_hole_at_location`
  * `notify_tree_manipulation`
  * `deactivate!`
