```
LithosphericPhases(Layers=[10 20 15], Phases=[1 2 3 4], Tlab=nothing )
```

This allows defining a layered lithosphere. Layering is defined from the top downwards.

# Parameters

  * Layers : The thickness of each layer, ordered from top to bottom. The thickness of the last layer does not have to be specified.
  * Phases : The phases of the layers, ordered from top to bottom.
  * Tlab   : Temperature of the lithosphere asthenosphere boundary. If specified, the phases at locations with T>Tlab are set to Phases[end].
