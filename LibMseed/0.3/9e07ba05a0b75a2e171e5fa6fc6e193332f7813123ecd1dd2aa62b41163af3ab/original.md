```
MseedTraceID
```

Container for several segments of continuous data for a single channel.

# Fields

  * `id`: `String` describing the source channel ID as a 'URN'.
  * `earliest::NanosecondDateTime`: Time of earliest sample in all segments.
  * `latest::NanosecondDateTime`: Time of latest sample in all segments.
  * `segments::Vector{MseedTraceSegment}`: Set of data segments.  Each must have the same data type.
