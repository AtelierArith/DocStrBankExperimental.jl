```
variable_pump_head_gain(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates bounded (by default) or unbounded head gain variables for pumps in in the network at subnetwork (or time) index `nw`, i.e., `g_pump[a]` for `a` in `pump`. Note that these variables are always nonnegative, since for each pump, there will never be negative head gain (i.e., pumps only increase head). Head gain is always directed from "node*fr" (i.e., the tail node of the arc) to "node*to" (i.e., the head node of the arc).
