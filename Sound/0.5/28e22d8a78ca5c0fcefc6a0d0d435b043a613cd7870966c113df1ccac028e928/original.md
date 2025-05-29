```
soundsc(sb::SampleBuf)
```

Play audio signal `sb` of type `SampleBuf` through default audio output device using the `PortAudio` package, after scaling the data to have values in `(-1,1)`.
