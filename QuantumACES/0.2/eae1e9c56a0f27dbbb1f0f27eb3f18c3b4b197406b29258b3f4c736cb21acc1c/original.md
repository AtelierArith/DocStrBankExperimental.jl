```
is_two_qubit(g::Gate; stim_supported::Bool = false)
```

Returns `true` if the gate `g` is a supported two-qubit gate, and `false` otherwise. If `stim_supported` is `true`, restrict to those gates also supported by Stim.
