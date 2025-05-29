```
scan_stdout(filout::String)
```

Scan a MITgcm standard output text file ("output.txt" or "STDOUT.0000") and return a NamedTuple of information collected.

  * packages : report of packages being compiled and used
  * params_time : initial time, model duation, output frequency, etc
  * params_grid : type of grid (Curvilinear, Cartesian, ...) and array sizes
  * params*files : type of output (use*mdsio, use_mnc) and array size (ioSize)
  * completed : true / false depending on the end of standard output file (filout)
