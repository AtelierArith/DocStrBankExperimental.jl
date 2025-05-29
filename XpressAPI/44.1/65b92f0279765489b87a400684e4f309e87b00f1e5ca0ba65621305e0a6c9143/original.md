```
XPRS_FORCEOUTPUT
```

Certain names in the problem object may be incompatible with different file formats (such as names containing spaces for LP files). (integer)

If the optimizer might be unable to read back a problem because of non-standard names, it will first attempt to write it out using an extended naming convention. If the names would not be possible to extend so that they would be reproducible and recognizable, it will give an error message and won't create the file. If the optimizer might be unable to read back a problem because of non-standard names, it will give an error message and won't create the file. This option may be used to force output anyway.

Default value: `0`

Values: 0 : Check format compatibility, and in case of failure try to extend names so that they are reproducible and recognizable. 1 : Force output using problem names as is. 2 : Always use 'x(' original name ')' in LP files to create a representation that can be read by Xpress. Default for problem having spaces in names 3 : Substitute spaces by the '_' character in LP files
