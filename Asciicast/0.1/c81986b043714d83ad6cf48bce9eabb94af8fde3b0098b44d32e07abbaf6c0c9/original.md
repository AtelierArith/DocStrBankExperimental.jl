```
Cast(file_or_io=IOBuffer(), header=Header(), start_time=time(); delay=0.0, loop=false)
```

Create a `Cast` object which represents an `asciicast` file (see [https://github.com/asciinema/asciinema/blob/asciicast-v2/doc/asciicast-v2.md](https://github.com/asciinema/asciinema/blob/asciicast-v2/doc/asciicast-v2.md) for the format).

  * Set `delay` to enforce a constant delay between events.
  * Set `loop` to `true` to loop continuously, or to an integer to loop a specified number of times. Only supported in the HTML `show` method for asciinema-player (not in the written file format, nor gif support, which currently always loops).

Use [`write_event!`](@ref) to write an event to the cast.
