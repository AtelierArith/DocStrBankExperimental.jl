```
mellanize(imagefile, side=500;
    lineweight       =  5.0, # multiply the grey value of a pixel [0,1] to get this width of line
    minlineweight    =  0.0,
    foregroundcolor  =  "black",
    backgroundcolor  =  "antiquewhite2",
    startradius      =  5.0,   # starting radius
    margin           =  5,
    tightness         = 2.0,  # controls how much the radius lengthens for each step,
    chord            =  2.0, # length of each stroke
    annotation       =  false,
    output           =  ""
    )
```

where `imagefile` is path of 8bit PNG or JPG, and `side` is the required image size.
