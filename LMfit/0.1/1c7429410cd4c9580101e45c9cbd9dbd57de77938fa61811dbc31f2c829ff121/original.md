```
fit(m::Model, y, ps::Parameters; kwargs...)
```

Fits the Model m to the data y, with parameters ps with the provided x values.  Note that the LMFit.py syntax is smarter in that the kw argument actually define the name of the paramteres that will be used for the x values  via the name of keyword arguments: 

so x=x would indicate that the name of the parameter in the function is actually x.
