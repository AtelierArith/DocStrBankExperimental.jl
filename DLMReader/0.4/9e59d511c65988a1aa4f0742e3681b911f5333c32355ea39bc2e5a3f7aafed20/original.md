```
filereader(path; [...])
```

Read a delimited file into `Julia`.

# Keyword arguments

  * `types`: User can pass the types of each column of the input file by using the `types` keyword argument. User may pass a vector of types which includes every type of each column, or may pass a dictionary of types for few selected columns.
  * `delimiter`: To change the default delimiter, user must pass the `delimiter` keyword argument. The `delimiter` keyword argument only accept `Char` as delimiter. Additionally, user can pass a vector of `Char` which causes `filereader` to use them as alternative delimiters.
  * `dlmstr`: This keyword argument is used to pass a string as the delimiter for values.
  * `ignorerepeated`: If it is set as `true`, repeated delimiters will be ignored.
  * `header`: User must set this as `false` if the first line of the input file is not the column header. Additionally, user can pass a vector of columns' name, which will be used as the columns' header.
  * `linebreak`: The `filereader` function use the value of this option as line separator. It can accept a `Char` or a vector of `Char` where the length of the vector is less than or equal two. For some rare cases user may need to pass this option to assist `filereader` in reading the input file.
  * `guessingrows`: This provide the number of lines to be used for types detection. The `filereader` function will detect the types of the column more accurately if user increase this value, however, it costs more computation time.
  * `fixed`: This option is used for reading fixed width files. User must pass a dictionary of columns' locations (as a range) for reading a fixed width file.
  * `quotechar`: If the texts are quoted in the input file, user must pass the quoted character via this keyword argument.
  * `escapechar`: Declaring the escape char for quoted text.
  * `dtformat`: User must pass the date format of DateTime columns if they are different from the standard format. The `dtformat` keyword argument accept a dictionary of values.
  * `int_base`: The `filereader` can read integers with given base. User must pass this information for a specific column.
  * `informat`: User can pass a dictionary which provides the information of the `informat` of selected columns.
  * `skipto`: It can be used to start reading a file from specific location.
  * `limit`: It can be used to limit the number of observations read from the input file.
  * `multiple_obs`: If it is set as `true`, the `filereader` function assumes there are more than one observation in each line of the input file.
  * `line_informat`: User can provide line informat via this keyword argument.
  * `buffsize`: User can provide any positive number for the buffer size. Each thread allocates the amount of `buffsize` and reads the values from the input file into it.
  * `lsize`: It indicated the line buffer size for reading the input files. For very wide table use may need to manually adjust this option. Its value must be less than `buffsize`.
  * `string_trim`: Setting this as `true` will trim the trailing blanks of strings before storing them into the output data set.
  * `makeunique`: If there are non-unique columns' names, this can resolve it by adding a suffix to the names.
  * `emptycolname`: If it is set to `true`, it generates a column name for columns with empty name.
  * `warn`: Control the maximum number of warning and information. Setting it to 0 will suppress warnings and information during reading the input file.
  * `eolwarn`: Control if the end-of-line character warning should be shown.
  * `threads`: For large files, the `filereader` function exploits all threads. However, this can be switch off by setting this argument as `false`.
  * `threshold`: The file size threshold (in bytes) which specifies the minimum file size for switching to the high performance algorithm. By default it is set to 2^26.
