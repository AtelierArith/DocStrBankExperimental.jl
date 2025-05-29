```
RunInfo(; creation_time=time(), inference_start=nothing, last_message_time=nothing, stop_sequence=nothing)
```

Tracks run statistics and metadata during the streaming process.

# Fields

  * `creation_time`: When the callback was created
  * `inference_start`: When the model started processing
  * `last_message_time`: Timestamp of the last received message
  * `stop_sequence`: The sequence that caused the generation to stop (if any)
