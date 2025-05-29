```
readdlm2(source; options...)
readdlm2(source, T::Type; options...)
readdlm2(source, delim::AbstractChar; options...)
readdlm2(source, delim::AbstractChar, T::Type; options...)
readdlm2(source, delim::AbstractChar, eol::AbstractChar; options...)
readdlm2(source, delim::AbstractChar, T::Type, eol::AbstractChar; options...)
```

Read a matrix from `source`. The `source` can be a text file, stream or byte array. Each line (separated by `eol`, this is `'\n'` by default) gives one row. The columns are separated by `';'`, another `delim` can be defined.

Pre-processing of `source` with regex substitution changes the decimal marks from `d,d` to `d.d`. For default `rs` the keyword argument `decimal=','` sets the decimal Char in the `r`-string of `rs`. When a special regex substitution tuple `rs=(r.., s..)` is defined, the argument `decimal` is not used. Pre-processing can be switched off with: `rs=()`.

In addition to stdlib readdlm(), data is also parsed for `Dates` formats, the `Time` format `"HH:MM[:SS[.s{1,9}]]"` and for complex and rational numbers. To deactivate parsing dates/time set: `dfs="", dtfs=""`. `locale` defines the language of day (`E`, `e`) and month (`U`, `u`) names.

The result will be a (heterogeneous) array of default element type `Any`. If `header=true` it will be a tuple containing the data array and a vector for the columnnames. Other (abstract) types for the data array elements could be defined. If data is empty, a `0×0 Array{T,2}` is returned.

With `tables=true`[, `header=true`] option[s] a `Tables` interface compatible `MatrixTable` with individual column types is returned, which for example can be used as Argument for `DataFrame()`.

# Additional Keyword Arguments

  * `decimal=','`: Decimal mark Char used by default `rs`, irrelevant if `rs`-tuple is not the default one
  * `rs=(r"(\d),(\d)", s"\1.\2")`: Regex (r,s)-tuple, the default change d,d to d.d if `decimal=','`
  * `dtfs="yyyy-mm-ddTHH:MM:SS.s"`: Format string for DateTime parsing
  * `dfs="yyyy-mm-dd"`: Format string for Date parsing
  * `locale="english"`: Language for parsing dates names
  * `tables=false`: Return `Tables` interface compatible MatrixTable if `true`
  * `dfheader=false`: 'dfheader=true' is shortform for `tables=true, header=true`
  * `missingstring="na"`: How missing values are represented

Find more information about `readdlm()` functionality and (keyword) arguments - which are also supported by `readdlm2()` - in `help` for `readdlm()`.

# Code Example

```jldoctest
julia> using ReadWriteDlm2

julia> A = Any[1 1.2; "text" missing];

julia> writedlm2("test.csv", A)

julia> readdlm2("test.csv")
2×2 Array{Any,2}:
 1        1.2
  "text"   missing
```
