```
is_unidirectional(l::Link)
```

Returns logic whether the link `l` can be used bidirectional or only unidirectional.

!!! note "Bidirectional flow in links"
    In the current stage, `EnergyModelsBase` does not include any links which can be used bidirectional, that is with flow reversal.

    If you plan to use bidirectional flow, you have to declare your own nodes and links which support this. You can then dispatch on this function for the incorporation.

