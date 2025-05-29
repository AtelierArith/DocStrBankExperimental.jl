```Julia
set_arg!(run::XRT.XRTWrap.Run, index, val)
set_arg!(run::XRT.XRTWrap.Run, index, val::XRT.AbstractBOArray)
set_arg!(run::XRT.XRTWrap.Run, index, val::XRT.XRTWrap.BO)

```

Set the argument for a kernel at the given index. Note, that this is a thin wrapper to the C++ API, so the indices start at 0!
