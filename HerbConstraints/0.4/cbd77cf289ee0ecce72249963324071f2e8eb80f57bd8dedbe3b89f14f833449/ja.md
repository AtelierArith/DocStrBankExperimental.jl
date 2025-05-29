```
abstract type Solver
```

抽象制約ソルバー。各ソルバーは少なくとも以下のフィールドを持つべきです：

  * `statistics::TimerOutput`
  * `fix_point_running::Bool`
  * `schedule::PriorityQueue{AbstractLocalConstraint, Int}`

各ソルバーは少なくとも以下を実装するべきです：

  * `post!`
  * `get_tree`
  * `get_grammar`
  * `set_infeasible!`
  * `isfeasible`
  * `HerbCore.get_node_at_location`
  * `get_hole_at_location`
  * `notify_tree_manipulation`
  * `deactivate!`
