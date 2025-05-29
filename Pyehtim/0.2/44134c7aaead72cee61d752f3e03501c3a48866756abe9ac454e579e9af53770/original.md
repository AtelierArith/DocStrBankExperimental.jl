```
scan_average(obs)
```

This homogenizes the scan times for an eht-imaging `Obsdata` object. This is needed because eht-imaging has a bug that will sometimes create very small scans and this can mess up both the closure construction and the gain scan times. Note that this is only a problem if we are fitting **scan averaged** data.
