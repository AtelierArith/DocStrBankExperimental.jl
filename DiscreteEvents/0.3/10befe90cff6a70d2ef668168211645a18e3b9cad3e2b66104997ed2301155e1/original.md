```
RTClock{E <: ClockEvent} <: AbstractClock
```

A real time clock checks every given period for scheduled events and executes them. It has a time in seconds since its start or last reset and uses system time for updating.

Real time clocks are controlled over channels. Multiple real time clocks can be setup with arbitrary periods (≥ 1 ms). Real time clocks should not be created directly but rather with `CreateRTClock`.

# Fields

  * `Timer::Timer`:     clock period in seconds, minimum is 0.001 (1 ms)
  * `clock::Clock`:     clock work
  * `cmd::Channel{T}`:  command channel to asynchronous clock
  * `back::Channel{T}`: back channel from async clock
  * `id::Int`:          arbitrary id number
  * `thread::Int`:      thread the async clock is living in
  * `time::Float64`:    clock time since start in seconds
  * `t0::Float64`:      system time at clock start in seconds
  * `T::Float64`:       clock period in seconds
