```
MPDModel
```

The MPD model stores the information contained in a .mpd or .ldr file. This includes a submodel tree (stored implicitly in a dictionary that maps model_name to SubModelPlan) and a part list. The first model in MPDModel.models is the main model. All the following are submodels of that model and/or each other.
