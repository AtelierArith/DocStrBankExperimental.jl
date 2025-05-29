```
getPath(path;
        names=path.names, tend=1.1*path.Tend, ntime=101, onlyPositions=false)
```

`path::PTP_path`を与えると、すべての`ntime`時間点に対して`tend`までの経路の時間系列を持つSignalTables.SignalTableを返します。
