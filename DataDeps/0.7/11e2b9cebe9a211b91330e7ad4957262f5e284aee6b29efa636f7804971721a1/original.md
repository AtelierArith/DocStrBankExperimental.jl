```
ManualDataDep(name, message)
```

A DataDep for if the installation needs to be handled manually. This can be done via Pkg/git if you put the dependency into the packages repo's `/deps/data` directory. More generally, message should give instructions on how to setup the data.
