```
rheologrun(log::RheoLog, d::Union{RheoTimeData,RheoFreqData,Nothing} = nothing)
```

execute all actions from the log. It applies them to the data `d` provided, or use the log's first action to reload/recreate it otherwise.
