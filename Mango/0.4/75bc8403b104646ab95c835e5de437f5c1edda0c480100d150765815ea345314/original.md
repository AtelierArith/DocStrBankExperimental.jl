Task data describing a periodic task. 

A periodic task is defined by an `interval_s` and optionally by a `condition`. The interval determines how long the delay is between the recurring action. The condition is a stopping condition (no argument) which shall return true if the task shall stop. 
