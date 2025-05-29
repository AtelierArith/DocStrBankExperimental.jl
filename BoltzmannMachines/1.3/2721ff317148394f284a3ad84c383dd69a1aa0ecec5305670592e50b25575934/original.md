```
monitored_fitdbm(x; ...)
```

This function performs the same training procedure as `fitdbm`, but facilitates monitoring: It fits an DBM model on the data set `x` using greedy layerwise pre-training and subsequent fine-tuning and collects all the monitoring results during the training. The monitoring results are stored in a vector of `Monitor`s, containing one element for each RBM layer and as last element the monitoring results for fine-tuning. (Monitoring elements from the pre-training of partitioned layers are again vectors, containing one element for each partition.) Both the collected monitoring results and the trained DBM are returned.

See also: `monitored_stackrbms`, `monitored_traindbm!`

# Optional keyword arguments:

  * `monitoring`: Used for fine-tuning. A monitoring function or a vector of monitoring functions that accept four arguments:

    1. a `Monitor` object, which is used to collect the result of the monitoring function(s)
    2. the DBM
    3. the epoch
    4. the data used for monitoring.

    By default, there is no monitoring of fine-tuning.
  * `monitoringdata`: a `DataDict`, which contains the data that is used for the  monitoring. For the pre-training of the first layer and for fine-tuning,  the data is passed directly to the `monitoring` function(s).  For monitoring the pre-training of the higher RBM layers,  the data is propagated through the layers below first.  By default, the training data `x` is used for monitoring.
  * `monitoringpretraining`: Used for pre-training. A four-argument function like  `monitoring`, but accepts as second argument an RBM.  By default there is no monitoring of the pre-training.
  * `monitoringdatapretraining`: Monitoring data used only for pre-training.  Defaults to `monitoringdata`.
  * Other specified keyword arguments are simply handed to `fitdbm`. For more information, please see the documentation there.

# Example:

```
using Random; Random.seed!(1)
xtrain, xtest = splitdata(barsandstripes(100, 4), 0.5)
monitors, dbm = monitored_fitdbm(xtrain;
    monitoringpretraining = monitorreconstructionerror!,
    monitoring = monitorlogproblowerbound!,
    monitoringdata = DataDict("Training data" => xtrain, "Test data" => xtest),
    # some arguments for `fitdbm`:
    nhiddens = [4; 3], learningratepretraining = 0.01,
    learningrate = 0.05, epochspretraining = 100, epochs = 50)
using BoltzmannMachinesPlots
plotevaluation(monitors[1]) # view monitoring of first RBM
plotevaluation(monitors[2]) # view monitoring of second RBM
plotevaluation(monitors[3]) # view monitoring fine-tuning
```
