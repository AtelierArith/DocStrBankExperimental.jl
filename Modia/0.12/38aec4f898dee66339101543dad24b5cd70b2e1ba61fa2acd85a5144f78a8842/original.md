```
getPath(path;
        names=path.names, tend=1.1*path.Tend, ntime=101, onlyPositions=false)
```

Given a `path::PTP_path`, return a SignalTables.SignalTable with the time series of the path over `time` up to `tend` for all `ntime` time points.
