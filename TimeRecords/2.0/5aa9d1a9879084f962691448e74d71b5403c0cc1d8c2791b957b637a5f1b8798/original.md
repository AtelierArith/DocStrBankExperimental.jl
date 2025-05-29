mapvalues!(f, ts::AbstractTimeSeries) -> ts

Maps callable "f" to each of the values in ts, modifying it in-place. Output must be the same type as input
