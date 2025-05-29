Holds information about current simulation state Contains the following fields:

  * `now`         current simulation time
  * `event_queue` priority queue of `Actions` planned to be executed
  * `state`       user defined subtype of `AbstractState` of the simulation
  * `monitor`     function that is called before event is triggered               must accept two arguments `Scheduler` and `Δ`, a difference               between time of event to be executed and time of last executed event

If two `Action`s have identical `when` time in `event_queue` then the order of their execution is undefined

When `monitor` is executed the event to happen is still on `event_queue`, but time is updated to time when the event is to be executed (i.e. `monitor` sees the state of the simulation just before the event is triggered). Therefore for calculating summary statistics `monitor` may assume that the simulation spent `Δ` time in this state. Function `monitor` should not modify `event_queue[1]` as EventSimulation assumes that the event to be triggered after `monitor` executes will not be modified. Additionally it it not guaranteed that `event_queue[1]` will be executed after `monitor` finishes because simulation might terminate earlier.
