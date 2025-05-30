```
start_reading(d::AbstractDiskDataProvider)
```

Initialize reading into the buffer. This function has to be called before the dataset is used. Reading will continue until you call `stop!` on the dataset. If the dataset is a [`ChannelDiskDataProvider`](@ref), this is a non-issue.
