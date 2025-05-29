```
nominal_srate(info::StreamInfo)
```

Return sampling rate of the stream `info`, according to the source (in Hz).

If a stream is irregularly sampled, this should be set to IRREGULAR_RATE.

Note that no data will be lost even if this sampling rate is incorrect or if a device has temporary hiccups, since all samples will be recorded anyway (except for those dropped by the device itself). However, when the recording is imported into an application, a good importer may correct such errors more accurately if the advertised sampling rate was close to the specs of the device.
