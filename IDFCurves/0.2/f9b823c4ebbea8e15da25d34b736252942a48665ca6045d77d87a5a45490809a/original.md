```
scalingtest(fd::Type{<:MarginalScalingModel}, data::IDFdata;
    tag_out::String, q::Integer)
```

Performs the testing procedure in order to state if the model fd may be rejected considering the data. It returns the p-value of the test. d_out is the duration to be put in the validation set. By default it will be set to the smallest duration in the data. q is the number of eigenvalues to compute when using the Zolotarev approximation for the p-value.
