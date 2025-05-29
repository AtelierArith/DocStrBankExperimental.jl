```
sector(centerpoint::Point, innerradius, outerradius,
        startangle, endangle, cornerradius;
       action:none)
```

Make an annular sector with rounded corners, basically a bent sausage shape, centered at `centerpoint`, and add it to the current path.

TODO: The results aren't 100% accurate at the moment. There are small discontinuities where the curves join.

TODO - return something more useful than a Boolean

The cornerradius is reduced from the supplied value if neceesary to prevent overshoots.
