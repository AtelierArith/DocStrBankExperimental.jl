```
TrainingArg(
    batchsize::Int64 
    lossf::Function
    lr::Float64
    epoch::Int64
    tv_split::Float64
    patience::Tuple{Int64,Int64} 
    device::Function
)
```

Return `TrainingArg` Type object with fields related to how network will be trained. batch size; loss function; learning rate; number of epoches; validation/training data split; patience for train loss plateau, patience for validation loss to increase.  Patiences are currently not applied when training and validating on generated training samples from uniform parameter distributions,  therefore training will stop when reaching the number of epoches.  The patience parameter will be considered in the future when training with real data or generated data with other distributions. 
