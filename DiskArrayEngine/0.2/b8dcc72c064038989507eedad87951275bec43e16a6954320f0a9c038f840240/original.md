```
interpolate_diskarray(a, conv)
```

Function to interpolate a diskarray along one or more dimensions. The interpolation is specifed by the list `conv` consisting of pairs of `dim_index => (source_axis,dest_axis)` values. For example, to interpolate  an  input array with dimensions (x,y,t) to new coordinates (x2,y2,t2) you can do

````julia #Old coordinates a = [i+j+k for i in 1:4, j in 1:5, k in 1:6] #source coordinates x = 5.0:5.0:20.0 y = 2.0:3.0:14.0 #target coordinates x2 = 5.0:0.5:20.0 y2 = 1.5:1.0:14.5 r = interpolate_diskarray(a,(1=>(x,x2),2=>(y,y2)))
