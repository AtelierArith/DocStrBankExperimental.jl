```
pad_array(m, nb; mode=:border)
```

Pads to the input array with either copying the edge value (:border) or zeros (:zeros)

Parameters

  * `m`: Array to be padded.
  * `nb`: Size of padding. Array of tuple with one (nb*left, nb*right) tuple per dimension.
  * `mode`: Padding mode (optional), defaults to :border.
