```
setelement!(mvis::MechanismVisualizer, element::VisualElement, name::AbstractString="<element>")
```

Attach the given visual element to the visualizer. The element's frame will determine how its geometry is attached to the scene tree, so that any other geometries attached to the same body will all move together.
