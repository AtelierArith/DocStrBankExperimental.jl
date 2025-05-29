```
readBiosemiStatus(edfh)
```

Export BDF Status channel data.

# Returns a Dict structure containing trigger data in the format:

  * Code => vector of triggerbit (Int),
  * Index => vector of index data (Int)
  * Onset => vector of onset times (Float)
  * Duration => vector of durations (Float)
