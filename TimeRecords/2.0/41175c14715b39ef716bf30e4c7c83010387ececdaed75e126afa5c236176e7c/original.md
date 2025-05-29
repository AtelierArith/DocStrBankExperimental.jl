```
interpolate(r1::TimeRecord, r2::TimeRecord, t::Real; order=0)
```

Interpolates from two time records (r1, r2) at point t using either zero-order hold (order=0) or saturated-linear (order=1)
