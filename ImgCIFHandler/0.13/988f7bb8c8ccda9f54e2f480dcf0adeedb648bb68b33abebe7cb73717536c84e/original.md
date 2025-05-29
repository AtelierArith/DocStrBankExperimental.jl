```
get_detector_axis_settings(imgcif,scanid,frameno)
```

Return the settings of all detector axes for the specified frame together with axis names and types in order names,types,settings. Values are computed from *diffrn*scan*axis information if _diffrn*scan*frame*axis is missing. Set `scanid` to `nothing` or `missing` if no scans are explicitly defined in the file.
