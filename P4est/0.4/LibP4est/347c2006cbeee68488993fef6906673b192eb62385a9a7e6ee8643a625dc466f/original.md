```
p4est_inspect
```

Data pertaining to selecting, inspecting, and profiling algorithms. A pointer to this structure is hooked into the `p4est` main structure.

The balance_ranges and balance_notify* times are collected whenever an inspect structure is present in `p4est`.

| Field                     | Note                                                                                                                                   |
|:------------------------- |:-------------------------------------------------------------------------------------------------------------------------------------- |
| use_balance_ranges        | Use sc_ranges to determine the asymmetric communication pattern. If *use*balance*ranges* is false (the default), sc_notify is used.    |
| use_balance_ranges_notify | If true, call both sc_ranges and sc_notify and verify consistency. Which is actually used is still determined by *use*balance*ranges*. |
| use_balance_verify        | Verify sc_ranges and/or sc_notify as applicable.                                                                                       |
| balance_max_ranges        | If positive and smaller than p4est_num ranges, overrides it                                                                            |
| balance_ranges            | time spent in sc_ranges                                                                                                                |
| balance_notify            | time spent in sc_notify                                                                                                                |
| balance_notify_allgather  | time spent in sc_notify_allgather                                                                                                      |
