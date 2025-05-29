```
begin_timed_section!([to::TimerOutput=DEFAULT_TIMER], label::String)
```

Start timing a section with the given label. Returns a `SectionTimeData` object that should be passed to `end_timed_section!` when the section is done.
