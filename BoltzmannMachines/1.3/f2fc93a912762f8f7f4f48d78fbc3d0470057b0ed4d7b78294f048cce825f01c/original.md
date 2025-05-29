```
monitored_traindbm!(dbm, x; ...)
```

This function performs the same training procedure as `traindbm!`, but facilitates monitoring: It performs fine-tuning of the given `dbm` on the data set `x` and collects monitoring results during the training in one `Monitor` object. Both the collected monitoring results and the trained `dbm` are returned.

# Optional keyword arguments:

  * `monitoring`: A monitoring function or a vector of monitoring functions that accept four arguments:

    1. a `Monitor` object, which is used to collect the result of the monitoring function(s)
    2. the DBM
    3. the epoch
    4. the data used for monitoring.

    By default, there is no monitoring.
  * `monitoringdata`: a `DataDict`, which contains the data that is used for  monitoring and passed to the `monitoring` functions(s).  By default, the training data `x` is used for monitoring.
  * Other specified keyword arguments are simply handed to `traindbm!`. For more information, please see the documentation there.

# Example:

```
using Random; Random.seed!(0)
xtrain, xtest = splitdata(barsandstripes(100, 4), 0.1)
dbm = stackrbms(xtrain; predbm = true, epochs = 20)
monitor, dbm = monitored_traindbm!(dbm, xtrain;
    monitoring = monitorlogproblowerbound!,
    monitoringdata = DataDict("Training data" => xtrain, "Test data" => xtest),
    # some arguments for `traindbm!`:
    epochs = 100, learningrate = 0.1)
using BoltzmannMachinesPlots
plotevaluation(monitor)
```
