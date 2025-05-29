```
timeseries(x::Node{{Union{Number, Point2}}})
```

Plots a sampled signal. Usage:

```julia
signal = Node(1.0)
scene = timeseries(signal)
display(scene)
# @async is optional, but helps to continue evaluating more code
@async while isopen(scene)
    # aquire data from e.g. a sensor:
    data = rand()
    # update the signal
    signal[] = data
    # sleep/ wait for new data/ whatever...
    # It's important to yield here though, otherwise nothing will be rendered
    sleep(1/30)
end

```
