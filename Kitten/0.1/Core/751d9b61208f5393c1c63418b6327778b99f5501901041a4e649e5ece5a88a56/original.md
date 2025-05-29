```
internalrequest(req::HTTP.Request; middleware::Vector=[], serialize::Bool=true, catch_errors::Bool=true)
```

Directly call one of our other endpoints registered with the router, using your own middleware and bypassing any globally defined middleware
