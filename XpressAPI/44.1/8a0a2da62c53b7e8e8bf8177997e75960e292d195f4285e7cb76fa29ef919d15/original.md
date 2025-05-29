```
XPRS_IISLOG
```

Selects how much information should be printed during the IIS procedure. (integer)

Please refer to Appendix for a more detailed description of the IIS logging format.

Default value: `1`, a progress log is printed

Values: 0 : The IIS procedure does not produce any output. 1 : Prints general information and a progress log of the deletion filter, including bounds on the size of the IIS and timing information. 2 : Complete logging, including the full progress log of all the subproblem solves in the deletion filter. This setting is recommended only for debugging as it may produce a lot of output.
