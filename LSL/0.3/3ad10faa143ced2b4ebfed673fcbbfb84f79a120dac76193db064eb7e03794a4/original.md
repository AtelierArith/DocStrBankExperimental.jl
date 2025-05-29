```
close_stream(inlet::StreamInlet)
```

Drop the current data stream.

All samples that are still buffered or in flight will be dropped and transmission and buffering of data for this inlet will be stopped. If an application stops being interested in data from a source (temporarily or not) but keeps the outlet alive, it should call lsl*close*stream() to not waste unnecessary system and network  resources.
