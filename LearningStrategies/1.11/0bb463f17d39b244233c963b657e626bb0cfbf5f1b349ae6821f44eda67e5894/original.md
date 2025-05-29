A LearningStrategy should implement at least one of the following methods:

  * `setup!(strat, model, data)`
  * `cleanup!(strat, model)`
  * `hook(strat, model, i)`
  * `finished(strat, model, data, i)`
  * `update!(model, strat, item)`
