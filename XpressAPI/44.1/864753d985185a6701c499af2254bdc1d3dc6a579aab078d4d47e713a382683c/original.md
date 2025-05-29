```
XPRS_GLOBALBOUNDINGBOX
```

If a nonlinear problem cannot be solved due to appearing unbounded, it can automatically be regularized by the application of a bounding box on the variables. (double)

If this control is set to a negative value, in a second solving attempt all original variables will be bounded by the absolute value of this control. If set to a positive value, there will be a third solving attempt afterwards, if necessary, in which also all auxiliary variables are bounded by this value.

Default value: `1.0E+06`

Values: 0 : Disabled. Problem will return unbounded. n<0 : Enabled. Apply lower and upper bounds of this magnitude to all original variables if initial LP is unbounded. n>0 : Enabled. Apply lower and upper bounds of this magnitude to all original and auxiliary variables if initial LP and first regularization are unbounded.
