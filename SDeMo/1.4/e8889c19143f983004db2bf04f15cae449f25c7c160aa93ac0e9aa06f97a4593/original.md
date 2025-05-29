```
StatsAPI.predict(sdm::SDM, X; threshold = true)
```

This is the main prediction function, and it takes as input an SDM and a matrix of features. The only keyword argument is `threshold`, which determines whether the prediction is returned raw or as a binary value (default is `true`).
