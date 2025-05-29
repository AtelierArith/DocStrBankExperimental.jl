```
is_unidirectional(n::Node)
```

Returns logic whether the node `n` can be used bidirectional or only unidirectional.

!!! note "Bidirectional flow in nodes"
    In the current stage, `EnergyModelsBase` does not include any nodes which can be used bidirectional, that is with flow reversal.

    If you plan to use bidirectional flow, you have to declare your own nodes and links that support this. You can then dispatch on this function for the incorporation.

