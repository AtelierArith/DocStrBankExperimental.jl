The `Player` class is used to define the features of the agents. We can create objects by indicating the parameters in order or by mentioning their names. 

```
Player(prior::Gaussian=Gaussian(MU,SIGMA), beta::Float64=BETA, gamma::Float64=GAMMA)
Player(;prior::Gaussian=Gaussian(MU,SIGMA), beta::Float64=BETA, gamma::Float64=GAMMA)
```

  * `prior` is the prior belief distribution of skill hypotheses
  * `beta` is the standar deviation of the agent performance
  * `gamma` is the uncertainty (standar deviation) added to the estimates as time progresses
