```
ROITrace
```

Represents the analysis results for a single ROI trace.

Fields:

  * `raw_trace`: The raw fluorescence trace
  * `dfof`: The ΔF/F trace after baseline correction
  * `t_series`: Time points for the trace
  * `stim_start_time`: Start time of the stimulus (s)
  * `stim_end_time`: End time of the stimulus (s)
  * `channel`: Channel index
  * `stimulus_index`: Index of the stimulus this trace corresponds to
  * `fit_parameters`: Parameters from curve fitting [amplitude, tau*on, tau*off, delay]
  * `is_significant`: Whether the response is significant
