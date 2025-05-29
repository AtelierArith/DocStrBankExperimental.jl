```
set_dispatch_doctor_preferences!(mode::String)
set_dispatch_doctor_preferences!(; luxcore::String="disable", luxlib::String="disable")
```

Set the dispatch doctor preference for `LuxCore` and `LuxLib` packages.

`mode` can be `"disable"`, `"warn"`, or `"error"`. For details on the different modes, see the [DispatchDoctor.jl](https://astroautomata.com/DispatchDoctor.jl/dev/) documentation.

If the preferences are already set, then no action is taken. Otherwise the preference is set. For changes to take effect, the Julia session must be restarted.
