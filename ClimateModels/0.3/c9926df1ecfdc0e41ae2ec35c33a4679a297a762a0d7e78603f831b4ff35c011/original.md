```
RandomWalker(x::AbstractModelConfig)
```

Random Walk in 2D over `NS` steps (100 by default). Result is provided as an array and a text file. 

By default, `RandomWalker.csv` will be created in `pathof(x)`. That folder itself is created by `setup`, possibly via `run` as below.

```
MC=ModelConfig(ClimateModels.RandomWalker)
run(MC)
```
