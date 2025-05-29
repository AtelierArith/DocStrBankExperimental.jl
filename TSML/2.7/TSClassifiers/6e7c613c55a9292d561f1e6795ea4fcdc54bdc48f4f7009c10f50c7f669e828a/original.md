```
TSClassifier(
   Dict(
      # training directory
      :trdirectory => "",
      :tstdirectory => "",
      :modeldirectory => "",
      :feature_range => 7:20,
      :juliarfmodelname => "juliarfmodel.serialized",
      # Output to train against
      # (:class).
      :output => :class,
      # Options specific to this implementation.
      :impl_args => Dict(
         # Merge leaves having >= purity_threshold CombineMLd purity.
         :purity_threshold => 1.0,
         # Maximum depth of the decision tree (default: no maximum).
         :max_depth => -1,
         # Minimum number of samples each leaf needs to have.
         :min_samples_leaf => 1,
         # Minimum number of samples in needed for a split.
         :min_samples_split => 2,
         # Minimum purity needed for a split.
         :min_purity_increase => 0.0
      )
   )
)
```

Given a bunch of time-series with specific types. Get the statistical features of each, use these as inputs to RF classifier with output as the TS type, train and test. Another option is to use these stat features for clustering and check cluster quality. If accuracy is poor, add more stat features and repeat same process as outlined for training and testing. Assume that each time-series is named based on their type which will be used as target output. For example, temperature time series will be named as temperature?.csv where ? is an integer. Loop over each file in a directory, get stat and  record in a dictionary/dataframe, train/test. Default to using RandomForest  for classification of data types.
