readsas(filename::AbstractString;         encoding::AbstractString = "",         convert*dates::Bool = true,         include*columns::Vector = [],         exclude*columns::Vector = [],         string*array*fn::Dict = Dict(),         number*array*fn::Dict = Dict(),         column*types::Dict = Dict{Symbol,Type}(),         verbose_level::Int64 = 1)

Read a SAS7BDAT file.

`Encoding` may be used as an override only if the file cannot be read using the encoding specified in the file.  If you receive a warning about unknown encoding then check your system's supported encodings from the iconv library e.g. using the `iconv --list` command.

If `convert_dates == false` then no conversion is made and you will get the number of days for Date columns (or number of seconds for DateTime columns) since 1-JAN-1960.

By default, all columns will be read.  If you only need a subset of the columns, you may specify either `include_columns` or `exclude_columns` but not both.  They are just arrays of columns indices or symbols e.g. [1, 2, 3] or [:employeeid, :firstname, :lastname]

String columns by default are stored in `SASLib.ObjectPool`, which is an array-like structure that is more space-efficient when there is a high number of duplicate values.  However, if there are too many unique items (> 10%) then it's automatically switched over to a regular Array.

If you wish to use a different kind of array, you can pass your array constructor via the `string_array_fn` dict.  The constructor must take a single integer argument that represents the size of the array. The convenient `REGULAR_STR_ARRAY` function can be used if you just want to use the regular Array{String} type.

For examples, `string_array_fn = Dict(:column1 => (n)->CategoricalArray{String}((n,)))` or `string_array_fn = Dict(:column1 => REGULAR_STR_ARRAY)`.

For numeric columns, you may specify your own array constructors using the `number_array_fn` parameter.  Perhaps you have a different kind of array to store the values e.g. SharedArray.

Specify `column_type` argument if any conversion is required.  It should be a Dict, mapping column symbol to a data type.

For debugging purpose, `verbose_level` may be set to a value higher than 1. Verbose level 0 will output nothing to the console, essentially a total quiet option.
