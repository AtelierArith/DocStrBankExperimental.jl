```
name(info::StreamInfo)
```

Return name of the stream `info`.

This is a human-readable name. For streams offered by device modules, it refers to the type of device or product series that is generating the data of the stream. If the source is an application, the name may be a more generic or specific identifier. Multiple streams with the same name can coexist, though potentially at the cost of ambiguity (for the recording app or experimenter).
