```
monitored_stackrbms(x; ...)
```

This function performs the same training procedure as `stackrbms`, but facilitates monitoring: It trains a stack of RBMs using the data set `x` as input to the first layer and collects all the monitoring results during the training in a vector of `Monitor`s, containing one element for each RBM layer. (Elements for partitioned layers are again vectors, containing one element for each partition.) Both the collected monitoring results and the stack of trained RBMs are returned.

# Optional keyword arguments:

  * `monitoring`: A monitoring function or a vector of monitoring functions that accept four arguments:

    1. a `Monitor` object, which is used to collect the result of the monitoring function(s)
    2. the RBM
    3. the epoch
    4. the data used for monitoring.

    By default, there is no monitoring.
  * `monitoringdata`: a `DataDict`, which contains the data that is used for  monitoring. For the first layer, the data is passed directly to the `monitoring`  function(s). For monitoring the training of the higher layers,  the data is propagated through the layers below first.  By default, the training data `x` is used for monitoring.
  * Other specified keyword arguments are simply handed to `stackrbms`. For more information, please see the documentation there.

# Example:

```
using Random; Random.seed!(0)
xtrain, xtest = splitdata(barsandstripes(100, 4), 0.5)
monitors, rbm = monitored_stackrbms(xtrain;
    monitoring = monitorreconstructionerror!,
    monitoringdata = DataDict("Training data" => xtrain, "Test data" => xtest),
    # some arguments for `stackrbms`:
    nhiddens = [4; 3], learningrate = 0.005, epochs = 100)
using BoltzmannMachinesPlots
plotevaluation(monitors[1]) # view monitoring of first RBM
plotevaluation(monitors[2]) # view monitoring of second RBM
```
