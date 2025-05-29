```
Parameter
```

Commandline argument which can only be distinguished by position, like `program par1 par2`. Different parameters are seperated by space. And other `Delimiter` can be used to discribe the input format.

contains:

  * `position`        position of the variable
  * `innername`       varname which will be the name of variable name after parse
  * `default`         default value (input as string)
  * `parsefmt`        parse pattern
  * `required`        whether throw error when not exist or not
  * `help`            help information
