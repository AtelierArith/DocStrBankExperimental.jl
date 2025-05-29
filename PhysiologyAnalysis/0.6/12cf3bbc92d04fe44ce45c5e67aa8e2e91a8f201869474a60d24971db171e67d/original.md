This function is the amount of time that a certain trace spends in a particular bandwith.      I think it will be similar to the pepperburg, So this may become that function     The "criterion" is the percent.      This function will measure how long a response takes to return to a specific criterion amount (iᵣ)         -By default iᵣ is set to 0.60. 

```
An intial problem is the tendancy for the function to pick up drift and other packets. We can eliminate non-sequential packets
For more information on this function see 
    Pepperburg & Cornwall et al. Light-dependent delay in the falling phase of the retinal rod photoresponse

Use: 
>>> rmaxes = saturated_response(data1_testA)
>>> Tᵣ = percent_recovery_interval(data1_testA, rmaxes)
```
