```
Problem(dev::Device=CPU(), MQGprob::FourierFlows.Problem; parameters...)
```

Construct a constant diffusivity problem on device `dev` using the flow from a `GeophysicalFlows.MultiLayerQG` problem as the advecting flow. The device `CPU()` is set as the default device.
