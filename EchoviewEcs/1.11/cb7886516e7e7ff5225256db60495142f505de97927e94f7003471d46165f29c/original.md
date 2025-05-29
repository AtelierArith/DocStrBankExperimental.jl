```
load(filename::AbstractString)
```

Loads an Echoview calibration supplement file, returning a `Vector` of `Dict`. Each `Dict` represents a transducer calibration with keys and values containing the various calibration settings.

See [Echoview calibration supplement files](http://support.echoview.com/WebHelp/Reference/File_formats/Echoview_calibration_supplement_files.html).
