```
readbla(filename)
```

Read a Blaise specification file for a fixed width ascii file. Returns a vector of 'Varspec' objects.

A simple example of a Blaise specification file looks like

```
datamodel testbla
 Fields
    var1        : integer[9]
    var2        : string[8]
    dummy[2]
    var3        : Real[8, 2]
    vars        : Array[2010..2050] of STRING[4]
endmodel
```
