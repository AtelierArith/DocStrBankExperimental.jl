```
settimecol!(D::GMTdataset; col::Int=0, time_system="", time_unit="", time_epoch="")
```

Set the time column of a `D` GMTdataset (or vector of GMTdatasets) to a given time system.

### Args

  * `D``: a GMTdataset or a vector of GMTdatasets

### Kwargs

  * `col`: is the column number of the time column. Attention, this is a MANDATORY option  If only `col` is provided (*i.e.*, no `time_xxx` options are used), then we only set internal  info to make `col` the time column. That is, we assume that `col` contains already time in seconds (Unix time)
  * `time_system`: is one of: "JD", "MJD", "J2000", "S1985", "UNIX", "RD0001", "RATA".  See the GMT manual for a description of these systems (https://docs.generic-mapping-tools.org/dev/gmt.conf.html#term-TIME_SYSTEM).
  * `time_epoch`: In ALTERNATIVE to `time_system` use the `time_epoch` AND `time_unit` options.  `time_epoch` a string of the form 'yyyy-mm-ddT[hh:mm:ss]' (Gregorian) or 'yyyy-Www-ddT[hh:mm:ss]' (ISO)
  * `time_unit`: is one of: "year", "month", "week", "day", "hour", "minute", "second"
