```
aws_autogen_style
```

Use [`aws_input_stream`](@ref) tester to test edge cases in systems that take input streams. You can make it behave in specific weird ways (e.g. fail on 3rd read).

There are a few ways to set what gets streamed. - source_bytes: if set, stream these bytes. - source_stream: if set, wrap this stream (but insert weird behavior like failing on 3rd read). - autogen_length: autogen streaming content N bytes in length.
