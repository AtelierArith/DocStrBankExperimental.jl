```
schedule(f::Function, scheduler, data::TaskData)
```

Schedule a function (no arguments) using the specific scheduler (mostly the agent scheduler). The  functino `f` is scheduled using the information in `data`, which specifies the way `f` will be  scheduled.
