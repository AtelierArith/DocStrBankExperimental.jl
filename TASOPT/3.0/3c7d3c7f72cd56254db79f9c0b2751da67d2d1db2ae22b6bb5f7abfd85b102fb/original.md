```
PayloadRange(ac_og, Rpts, Ppts, filename, OEW, itermax)
```

Function to plot a payload range diagram for an aircraft

!!! details "🔃 Inputs and Outputs"
    **Inputs:**

      * `ac_og::aircraft`: Aircraft structure for payload range diagram.
      * `Rpts::Int64`: Density of ranges to be plot (Optional).
      * `Ppts::Int64`: Density of payloads to be plot (Optional).
      * `filename::String`: filename string for the plot to be stored (Optional).
      * `OEW::Bool`: Whether to have OEW+Payload on the y-axis or just Payload (Optional).
      * `itermax::Int64`: Max Iterations for fly_mission! loop (Optional).
      * `initializes_engine::Boolean`: Use design case as initial guess for engine state if true (Optional)
      * `Ldebug::Bool`: verbosity flag. false by default, hiding outputs as PR sweeps progress (Optional).

