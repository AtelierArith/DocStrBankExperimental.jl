`ExponentialQueue()` keeps an updatable queue of up to `N` events with ids `1...N` and contant rates Q[1] ... Q[N].  This is intended for sampling in continuous time.

julia> Q = ExponentialQueue() ExponentialQueue(Accumulator{Float64, +, zero}([Float64[]]), [0, 0, 0, 0, 0, 0, 0, 0, 0, 0  …  0, 0, 0, 0, 0, 0, 0, 0, 0, 0], Int64[])

julia> Q[1] = 1.2 #updates rate of event 1 1.2

julia> Q[55] = 2.3 #updates rate of event 55 2.3

julia> i,t = pop!(Q) # gets time and id of next event and remove it from the queue (55, 0.37869716808319576)

See also: `ExponentialQueueDict`
