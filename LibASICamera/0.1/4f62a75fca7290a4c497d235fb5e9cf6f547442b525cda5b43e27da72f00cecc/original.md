```
get_gain_offset(id::Integer)
```

Get the presets for offset and gain values at different "sweet spots".

# Args:

```
id: Camera id
```

# Returns:

```
A dictionary containing:
    1. The offset at highest dynamic range
    2. The offset at unity gain
    3. The gain with lowest readout noise
    4. The offset with lowest readout noise
```

# Throws:

```
ASIError
```
