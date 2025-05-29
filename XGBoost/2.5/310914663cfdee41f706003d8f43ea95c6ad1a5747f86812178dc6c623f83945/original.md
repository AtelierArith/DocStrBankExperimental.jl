```
updateone!(b::Booster, data; round_number=getnrounds(b)+1,
           watchlist=Dict("train"=>data), update_feature_names=false
          )
```

Run one round of gradient boosting with booster `b` on data `data`.  `data` can be any object that is accepted by a [`DMatrix`](@ref) constructor.  `round_number` is the number of the current round and is used for logs only.  Info logs will be printed for training sets in `watchlist`; keys give the name of that dataset for logging purposes only.
