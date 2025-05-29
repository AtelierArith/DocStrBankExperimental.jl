```
getPath(path;
        names=path.names, tend=1.1*path.Tend, ntime=101)
```

Given a `path::PTP_path`, return a dictionary with the time series of the path over `time` up to `tend` for all `ntime` time points.
