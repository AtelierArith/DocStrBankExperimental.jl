```
SeisMute(d; <keyword arguments>) -> Array{Real,2}
```

Mute trace noise before the first arrival. The muting function depends on the offset between source and receiver and the velocity of the first layer as t*mute = t*0 + offset/v1.

# Arguments

  * `d`: Array of input traces.

# Keyword arguments

  * `offset=[0.]`: Vector of distances between source and receiver.
  * `tmute=0.`: initial muting time
  * `vmute=1500.`: Velocity of the first layer.
  * `taper=0.1`: Taper of the muting function
  * `dt::Real=0.004`: sampling interval in secs.
