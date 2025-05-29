```
bw_opt_kde(pts, test_pts; test_low=-1, test_high=1)
```

Will return a KDE based on `pts` whose bandwidth factor maximizes the likelihood of `test_pts`.

`test_low` and `test_high` are the bounds on the natural log of the bandwidth factor for the optimizing search. 
