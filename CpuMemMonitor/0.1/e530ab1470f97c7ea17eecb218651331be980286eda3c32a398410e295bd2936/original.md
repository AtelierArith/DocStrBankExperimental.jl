```
function start_monitor(
    pid::Int64,
    fn::String; # file name used for saving info
    iterations::Int64 = 8,
    interval::Int64 = 1,
    outer_interval::Int64 = 3600
)

Save CPU and MEM info to two files, respectively.
```
