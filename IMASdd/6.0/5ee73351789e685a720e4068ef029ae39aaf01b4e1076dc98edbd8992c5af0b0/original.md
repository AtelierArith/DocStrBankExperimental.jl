```
cocos_transform(@nospecialize(ids::IDS), field::Symbol)
```

Return Vector of strings with cocos_transform for a given IDS location

  * empty vector for COCOS transforms that have not been manually assigned
  * one element vector filled with

      * `""` for no COCOS transforms
      * `"?"` for COCOS transforms that should have been manually assigned but were not
      * other strings, defining the cocos transformations as per the `CoordinateConventions.jl` package
