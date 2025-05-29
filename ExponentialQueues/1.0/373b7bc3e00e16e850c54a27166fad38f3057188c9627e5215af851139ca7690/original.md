`ExponentialQueueDict{K}` keeps an updatable queue of elements of type `K` with contant rates Q[k].  This is intended for sampling in continuous time.

julia> Q = ExponentialQueueDict{Int}() ExponentialQueueDict(Pair{Int64, Float64}[])

julia> Q[1] = 1.2 # updates rate of event 1 1.2

julia> Q[55] = 2.3 # updates rate of event 55 2.3

julia> i,t = pop!(Q) # gets time and id of next event and remove it from the queue (55, 0.37869716808319576)

See also: `StaticExponentialQueue` and `ExponentialQueue` for slightly more  efficient queues for the case `K == Int`
