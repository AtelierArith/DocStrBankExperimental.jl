Scheduler <: AbstractScheduler

  * `events`: a priority queue of events
  * `time`: current time of the system
  * `running`: simulation can run if true
  * `trace`: will print out the events if true
  * `store`: will store a vector of completed events if true
  * `complete_events`: an optional vector of completed events
