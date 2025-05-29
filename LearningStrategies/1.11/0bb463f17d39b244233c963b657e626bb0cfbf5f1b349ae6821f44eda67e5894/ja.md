A LearningStrategyは、以下のメソッドのうち少なくとも1つを実装する必要があります：

  * `setup!(strat, model, data)`
  * `cleanup!(strat, model)`
  * `hook(strat, model, i)`
  * `finished(strat, model, data, i)`
  * `update!(model, strat, item)`
