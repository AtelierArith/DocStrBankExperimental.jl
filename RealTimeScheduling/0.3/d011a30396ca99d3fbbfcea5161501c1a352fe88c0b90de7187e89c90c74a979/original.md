```
MeetRow{T}(meet::T, window::T)
```

Weakly hard constraint specifying that a task meets `meet` deadlines in a row in any window of size `window`.  Must satisfy `0 <= meet <= window`.
