```
shallow_copy_sim(CH::ControlChart)
```

Create a shallow copy of a control chart, so that only the statistic and the control limit are copied. This is done to prevent copying eventual Phase 2 data multiple times and thus reduce computational effort when optimizing the control limit and the chart tuning parameters.
