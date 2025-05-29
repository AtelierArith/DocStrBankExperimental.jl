```
SimpleGenerator <: AbstractGenerator
```

Default implementation for `generate`. It simply enumerates context snippets and runs `aigenerate` (no refinement).

It uses `ContextEnumerator`, `SimpleAnswerer`, `NoRefiner`, and `NoPostprocessor` as default `contexter`, `answerer`, `refiner`, and `postprocessor`.
