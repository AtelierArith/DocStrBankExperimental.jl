```
write(filename::String, blafilename::String, table)
```

Write the table to a fixed width ascii file. The blafile contains the specifications of the file in the Blaise format.

Using the datatype, length and if relevant the decimals from the specification a conversion function is generated to write a single value using the required width. For String, Integer, Real and Dummy there are conversion-functions generated by *makewrite*.  For other datatypes, the required generator must be provided.
