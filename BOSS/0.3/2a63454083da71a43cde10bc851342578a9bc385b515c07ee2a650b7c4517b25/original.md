If a `BossCallback` is provided to `BossOptions`, the callback is called once before the BO procedure starts, and after each iteration.

All callbacks *should* implement:

  * (::CustomCallback)(::BossProblem;       ::ModelFitter,       ::AcquisitionMaximizer,       ::AcquisitionFunction,       ::TermCond,       ::BossOptions,       first::Bool,   )

The kwarg `first` is true only on the first callback before the BO procedure starts.

See `PlotCallback` for an example usage of a callback for plotting.
