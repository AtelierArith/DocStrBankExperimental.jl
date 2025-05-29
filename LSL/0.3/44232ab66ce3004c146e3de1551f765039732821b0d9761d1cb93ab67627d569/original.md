```
StreamInfo(name = "untitled";
           type = "", 
           channel_count = 1,
           nominal_srate = LSL_IRREGULAR_RATE,
           channel_format = Float32,
           source_id = "")
```

Construct a new stream information object.

Core stream information is specified here. Any remaining meta-data can be added later.

# Keyword arguments

  * `name::String`: Name of the stream. Describes the device (or product series)                     that this stream makes available (for use by programs, experimenters or                 data analysts). Cannot be empty.
  * `type::String`: Content type of the stream. Please see https://github.com/sccn/xdf/wiki/Meta-Data                 (or web search for: XDF meta-data) for pre-defined content-type names, but                 you can also make up your own. The content type is the preferred way to                 find streams (as opposed to searching by name).
  * `channel_count::Integer`:   Number of channels per sample. This stays constant for the                             lifetime of the stream.
  * `nominal_srate::Number`:    The sampling rate (in Hz) as advertised by the datasource, if                             regular (otherwise set to LSL*IRREGULAR*RATE).
  * `channel_format::DataType`: Format/type of each channel.If your channels have different                             formats, consider supplying multiple streams or use the                             largest type that can hold them all (such as Float64).
  * `source_id::String`:       Unique identifier of the source or device, if available                             (such as the serial number). Allows recipients to recover from                             failure even after the serving app or device crashes. May in                             some cases also be constructed from device settings.
