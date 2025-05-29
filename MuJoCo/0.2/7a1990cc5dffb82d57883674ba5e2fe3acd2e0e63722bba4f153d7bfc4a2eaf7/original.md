```
load_model(path)
```

Determines the type of file by the extension and loads the model into memory.

To use this model in a simulator, you will also need the corresponding data, obtained using [`init_data`](@ref).

Expected files types: 'xml', 'mjcf', or 'mjb' (or uppercase variants).

# Examples

```julia
model = load_model(MuJoCo.humanoid_model_file())
data = init_data(model)
```
