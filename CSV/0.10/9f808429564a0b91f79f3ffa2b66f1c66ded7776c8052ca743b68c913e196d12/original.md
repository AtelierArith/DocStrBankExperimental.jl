CSV provides fast, flexible reader & writer for delimited text files in various formats.

Reading:

  * `CSV.File` reads delimited data and returns a `CSV.File` object, which allows dot-access to columns and iterating rows.
  * `CSV.read` is similar to `CSV.File` but used when the input will be passed directly to a sink function such as a `DataFrame`.
  * `CSV.Rows` reads delimited data and returns a `CSV.Rows` object, which allows "streaming" the data by iterating and thereby has a lower memory footprint than `CSV.File`.
  * `CSV.Chunks` allows processing extremely large files in "batches" or "chunks".

Writing:

  * `CSV.write` writes a [Tables.jl interface input](https://github.com/JuliaData/Tables.jl) such as a `DataFrame` to a csv file or an in-memory IOBuffer.
  * `CSV.RowWriter` creates an iterator that produces csv-formatted strings for each row in the input table.

Here is an example of reading a csv file and passing the input to a `DataFrame`:

```julia
using CSV, DataFrames
ExampleInputDF = CSV.read("ExampleInputFile.csv", DataFrame)
```

Here is an example of writing out a `DataFrame` to a csv file:

```julia
using CSV, DataFrames
ExampleOutputDF = DataFrame(rand(10,10), :auto)
CSV.write("ExampleOutputFile.csv", ExampleOutputDF)
```
