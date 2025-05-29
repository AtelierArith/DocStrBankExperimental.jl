```
GenericSolver
```

可行な部分プログラムを[`SolverState`](@ref)に保持します。[`ProgramIterator`](@ref)は、以下のツリー操作を使用して部分ツリーを操作できます。

  * `substitute!`
  * `remove!`
  * `remove_below!`
  * `remove_above!`
  * `remove_all_but!`

各[`SolverState`](@ref)は独立した伝播プログラムを保持します。プログラムイテレータは、以下を使用して状態間を自由に行き来できます。

  * `new_state!`
  * `save_state!`
  * `load_state!`
