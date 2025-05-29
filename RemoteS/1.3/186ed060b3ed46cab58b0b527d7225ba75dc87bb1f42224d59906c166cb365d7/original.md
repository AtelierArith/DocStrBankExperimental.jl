```
reportbands(in; [layers=Int[]])
```

or

```
reportbands(in, layer;)
```

Report the Bands description of the `in` input argument. This can be a GMTimage, a GMTgrid or a file name (a String) of  a 'cube' file. Normally one made with the `cutcube` function. When the use conditions of this function are not met, either a warning or an error message (if too deep to be caught as a warning) will be issued.

  * `layers`: When this optional parameter is used, report the description of the bands in the vector `layers`
  * `layer`: A scalar with a unique band number. Alternative form to `reportbands(in, layers=[layer])`

Returns a string vector.
