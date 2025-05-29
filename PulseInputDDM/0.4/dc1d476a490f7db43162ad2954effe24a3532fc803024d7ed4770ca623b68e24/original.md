```
bin_clicks(clicks)
```

Bins clicks, based on dt (defaults to 1e-2). 'centered' determines if the bin edges occur at 0 and dt (and then ever dt after that), or at -dt/2 and dt/2 (and then every dt after that). If the former, the bins align with the binning of spikes in the neural model. For choice model, the latter is fine.
