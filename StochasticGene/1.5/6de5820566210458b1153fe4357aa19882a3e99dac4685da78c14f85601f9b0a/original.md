```
simulate_trace_data(datafolder::String; ntrials::Int=10, r=[0.038, 1.0, 0.23, 0.02, 0.25, 0.17, 0.02, 0.06, 0.02, 0.000231, 30, 20, 200, 100, 0.8], transitions=([1, 2], [2, 1], [2, 3], [3, 1]), G=3, R=2, S=2, insertstep=1, onstates=Int[], interval=1.0, totaltime=1000.0)
```

create simulated trace files in datafolder
