```
channel_depolarizing(v::Real, d::Integer = 2)
```

Return the Kraus operator representation of the depolarizing channel of dimension `d`. It replaces a single qudit by the completely mixed state with probability '1-v'.
