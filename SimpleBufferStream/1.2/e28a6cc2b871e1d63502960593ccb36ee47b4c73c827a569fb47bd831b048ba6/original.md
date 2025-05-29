```
BufferStream
```

Simple buffered stream that appends data to an internal chunk list and allows for easy, simultaneous reading of that data.  Intended for shuffling data between tasks.  Best performance is achieved by using `readavailable()`, which avoids copies on reads.
