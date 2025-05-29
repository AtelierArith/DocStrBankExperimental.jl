```
epoch_iterator(edfh, epochsecs; channels, startsec, endsec, physical)
```

Make an iterator for EEG epochs of a given duration between start and stop times.

# Required arguments

  * edfh BEDFPlus struct
  * epochsecs second duration of each epoch

# Optional arguments

  * channels List of channel numbers for data, defaults to all signal channels
  * startsec Starting position from 0 at start of file, defaults to file start
  * endsec Ending position in seconds from start of *file*, defaults to file end
  * physical Whether to return data as translated to the physical units, defaults to true
