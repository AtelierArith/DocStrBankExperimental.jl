```
abaco_init(onresult; handle=nothing, interval::Int=900, ages::Int=4, emitone=true)::Context
```

Initialize the abaco context:

  * `onresult`: function callback that gets called each time a formula value is computed.
  * `handle`: user defined object.            If handle is defined it is the first argument of `onresult`, default to `nothing`.
  * `interval`: the span interval in seconds, default to 900 seconds (15 minutes).             If interval is equal to -1 there is just one infinite time span.
  * `ages`: the number of active rops managed by the abaco. Default to 4.         If `interval` is equal to -1 `ages`  is not applicable because it loses meaning.
  * `emitone`: if `true` emits for each time span at most 1 formula value,             otherwise emits a new result at every new inputs. Defaut to `true`

Example 1: defining `onresult` callback that uses of an handle object.

```
# the handle object is a socket
sock = connect(3001)

function onresult(handle, ts, ne, formula_name, value, inputs)
    # build a pkt message from ts, ne, ...
    pkt = ...
    write(sock, pkt)
end
```

Example 2: defining `onresult` callback that doesn't use an handle object.

```julia
abaco = abaco_init(onresult, handle=sock)

function onresult(ts, ne, formula_name, value, inputs)
    @info "[$ts][$ne] function $fname=$value"
end

abaco = abaco_init(onresult)
```
