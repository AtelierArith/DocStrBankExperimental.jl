```
@usingModiaPlot()
```

Execute `using XXX`, where `XXX` is the Plot package that was activated with `usePlotPackage(plotPackage)`. So this is similar to @usingPlotPackage (from SignalTables, that is reexported from Modia).

There is, however, a difference when XXX = "SilentNoPlot":

  * @usingPlotPackage() executes `using SignalTables.SilentNoPlot` and therefore requires that package `SignalTables` is available in your environment.
  * @usingModiaPlot() executes `using Modia.SignalTables.SilentNoPlot` and therefore requires that package `Modia` is available in your environment.

Therefore, when working with Modia it is better to use `@usingModiaPlot()`.
