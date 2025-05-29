```
extract_largest_component!(mol::SimpleMolGraph) -> Nothing
```

Return the largest connected component of the molecular graph.

This should be useful when you want to remove salt and water molecules from the molecular graph simply. On the other hand, this can remove important components from the mixture so carefully apply this preprocess method.
