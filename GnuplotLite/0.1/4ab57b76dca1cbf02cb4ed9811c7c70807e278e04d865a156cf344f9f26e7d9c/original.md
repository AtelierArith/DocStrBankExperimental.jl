```
gnuplot(persist = true, echo = false)
```

The main constructor for a `Gnuplot` instance. This starts the `gnuplot` process and creates a channel to which commands can be sent.

The `persist` argument make sure that any interactive window remains open, even if we have closed the pipe to the Gnuplot process.

The `echo` argument is for debugging. If enabled, all commands send to this instance are also echoed to `stdout`.
