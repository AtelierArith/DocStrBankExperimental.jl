```
show_next_transition(io::IO=stdout, zdt::ZonedDateTime)
show_next_transition(io::IO=stdout, tz::TimeZone=localzone())
```

Display useful information about the next time zone transition (typically due to daylight-savings time). Information displayed includes:

  * Transition Date: the local date at which the transition occurs (2018-10-28)
  * Local Time Change: the way the local clock with change (02:00 falls back to 01:00) and   the direction of the change ("Forward" or "Backward")
  * Offset Change: the standard offset and DST offset that occurs before and after the  transition
  * Transition From: the instant before the transition occurs
  * Transition To: the instant after the transition occurs

```julia
julia> show_next_transition(ZonedDateTime(2018, 8, 1, tz"Europe/London"))
Transition Date:   2018-10-28
Local Time Change: 02:00 → 01:00 (Backward)
Offset Change:     UTC+0/+1 → UTC+0/+0
Transition From:   2018-10-28T01:59:59.999+01:00 (BST)
Transition To:     2018-10-28T01:00:00.000+00:00 (GMT)

julia> show_next_transition(ZonedDateTime(2011, 12, 1, tz"Pacific/Apia"))
Transition Date:   2011-12-30
Local Time Change: 00:00 → 00:00 (Forward)
Offset Change:     UTC-11/+1 → UTC+13/+1
Transition From:   2011-12-29T23:59:59.999-10:00
Transition To:     2011-12-31T00:00:00.000+14:00
```
