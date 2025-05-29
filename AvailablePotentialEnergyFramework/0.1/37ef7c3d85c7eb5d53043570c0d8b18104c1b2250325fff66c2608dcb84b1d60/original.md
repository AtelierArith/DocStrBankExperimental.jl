```
shifter!(dest,array,time,domain_center,peak)
```

Stores in `dest` an array in which a pressure perturbation center is displaced to the center of the domain using circshift. Using it may assume periodic domain. Receives and SAM 3D+time or 2D+time array and two tuples, the (x,y) indices of the domain center, and the (x,y) indices of the location of the pressure perturbation peak.
