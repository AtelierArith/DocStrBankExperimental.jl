`clicks(b::BitlyToken,link; summary=false,unit="day",units=-1,size=50)`

Get click information for shortened link `link`.

`summary=true` provides a single count, otherwise returns a time series.

`unit` can be `"minute"`,`"hour"`,`"day"`,`"week"`,`"month"`.

`units` is an integer representing the number of time units to query data for. Pass `-1` to return all units available.

`size` is the quantity of items to be returned.

Returns a `Dict`.
