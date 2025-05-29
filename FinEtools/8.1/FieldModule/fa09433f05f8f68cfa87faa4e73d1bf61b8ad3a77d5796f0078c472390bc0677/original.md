```
setebc!(self::F)
```

Set the EBCs (essential boundary conditions).

All essential boundary conditions are CLEARED.

Note:  Any call to `setebc!()` potentially changes the current assignment which degrees of freedom are free and which are fixed and therefore is presumed to invalidate the current degree-of-freedom numbering.
