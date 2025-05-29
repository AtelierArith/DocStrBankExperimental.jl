```
type(info::StreamInfo)
```

Return the content type of the stream `info`.

The content type is a short string such as "EEG", "Gaze" which describes the content carried by the channel (if known). If a stream contains mixed content this value need not be assigned but may instead be stored in the description of channel types. To be useful to applications and automated processing systems using the recommended content types is preferred. Content types usually follow those pre-defined in https://github.com/sccn/xdf/wiki/Meta-Data (or web search for: XDF meta-data).
