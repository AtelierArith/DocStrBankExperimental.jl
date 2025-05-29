```
createRTClock(T::Float64, id::Int, thrd::Int=nthreads(); ch_size::Int=256)
```

Create, start and return a real time Clock.

The clock takes the current system time and starts to count in seconds with the given period `T`. Events or sampling functions can then be scheduled to it.

# Arguments

  * `T::Float64`:           period (clock resolution) in seconds, T ≥ 0.001
  * `id::Int`:              clock identification number other than 0:nthreads()
  * `thrd::Int=nthreads()`: thread, the clock task should run in
  * `ch_size::Int=256`:     clock communication channel size
