TimeSeriesCollector{T}(interval::Second, delay::Second, timer::RefValue{DateTime}, data::Dict{String, TimeSeries{T}})

Used to collect tagged time records Pair{String=>TimeRecord{T}} arriving mostly in order, designed to be taken at 'interval'

  * 'interval' is the collection interval (or window size that data will be fed to your algorithm)      when set to zero, the interval will be the distance between timestamps
  * 'delay' is the amount of time we wait beyond the interval to collect data.       This helps make algorithms robust against slightly out-of-order data
  * 'timer' is a DateTime reference that indicates the beginning of the next collection interval
  * 'data' is a Dict of TimeSeries that stores collected data.
