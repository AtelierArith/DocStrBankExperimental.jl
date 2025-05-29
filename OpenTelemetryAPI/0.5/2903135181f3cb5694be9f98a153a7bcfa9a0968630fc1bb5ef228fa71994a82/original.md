```
end_span!([s=current_span()], [t=UInt(time()*10^9)])
```

Set the end time of the span and trigger span processors. Note `t` is the nanoseconds.
