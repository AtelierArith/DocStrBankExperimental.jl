```
METRLA(; num_timesteps_in::Int = 12, num_timesteps_out::Int=12, dir=nothing, normalize = true)
```

The METR-LA dataset from the [Diffusion Convolutional Recurrent Neural Network: Data-Driven Traffic Forecasting](https://arxiv.org/abs/1707.01926) paper.

`METRLA` is a graph with 207 nodes representing traffic sensors in Los Angeles. 

The edge weights `w` are contained as a feature array in `edge_data` and represent the distance between the sensors. 

The node features are the traffic speed and the time of the measurements collected by the sensors, divided into `num_timesteps_in` time steps. 

The target values are the traffic speed of the measurements collected by the sensors, divided into `num_timesteps_out` time steps.

The `normalize` flag indicates whether the data are normalized using Z-score normalization.
