```
async_latest(observable::AbstractObservable, n=1)
```

Returns an `Observable` which drops all but the last `n` updates to `observable` if processing the updates takes longer than the interval between updates.

This is useful if you want to pass the updates from, say, a slider to a plotting function that takes a while to compute. The plot will directly compute the last frame skipping the intermediate ones.

# Example:

```
observable = Observable(0)
function compute_something(x)
    for i=1:10^8 rand() end # simulate something expensive
    println("updated with $x")
end
o_latest = async_latest(observable, 1)
on(compute_something, o_latest) # compute something on the latest update

for i=1:5
    observable[] = i
end
```
