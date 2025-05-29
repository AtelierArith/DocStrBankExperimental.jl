```
F8"some string"
```

String macro for compatible with FORTRAN strings `FortranString{UInt8}`.

The `'d'` and `"qq"` flag can be used to emulate behaviour fortran strings in double quotes, where the double quotes inside such strings must be doubled:

```
F8"Use \"\"doubled\"\""qq
```

The `'q'` flag indicates the emulation of Fortran strings in single quotes:

```
F8"Can''t be with only single quote inside"q
```
