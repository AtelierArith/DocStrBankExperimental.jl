```
find_channel(d::AbstractDeviceOrTrigger, name_or_id, is_output = false)
```

Find an IIO channel by its name or ID.

# Parameters

  * `d` : The device instance
  * `name_or_id` : The name or ID of the channel to find
  * `is_output` : Set to true to search for an output channel

# Returns

  * The IIO channel as `Channel`
