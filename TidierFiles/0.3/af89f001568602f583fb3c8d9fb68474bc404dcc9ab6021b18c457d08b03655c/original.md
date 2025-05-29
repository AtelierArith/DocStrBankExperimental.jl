```
read_gsheet(spreadsheet_id::String; 
             sheet::String="Sheet1", 
             range::String="", 
             col_names::Bool=true, 
             skip::Int=0, 
             n_max::Int=1000, 
             col_select=nothing, 
             missing_value::String="")
```

Read data from a Google Sheet into a DataFrame.

# Arguments

  * `spreadsheet_id::String`: The unique identifier of the Google Sheet or the full URL.
  * `sheet::String`: The name of the sheet to read from. Defaults to "Sheet1".
  * `range::String`: The range of cells to read (e.g., "A1:D10"). Defaults to an empty string, which reads the entire sheet.
  * `col_names::Bool`: Indicates whether the first row should be used as column names. Defaults to true.
  * `skip::Int`: Number of rows to skip before starting to read data. Defaults to 0.
  * `n_max::Int`: Maximum number of rows to read after skipping. Defaults to Inf (read all available rows).
  * `col_select`: List of column names or indices to select specific columns. Defaults to nothing (all columns).
  * `missing_value::String`: Value to represent missing data. Defaults to an empty string.

# Examples

```julia
julia> connect_gsheet("your_client_id", "your_client_secret")

julia> public_sheet = "https://docs.google.com/spreadsheets/d/1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms/edit?gid=0#gid=0";

julia> read_gsheet(public_sheet, sheet="Class Data", n_max=5)
5×6 DataFrame
 Row │ Student Name  Gender  Class Level   Home State  Major    Extracurricular Activity 
     │ String        String  String        String      String   String                   
─────┼───────────────────────────────────────────────────────────────────────────────────
   1 │ Alexandra     Female  4. Senior     CA          English  Drama Club
   2 │ Andrew        Male    1. Freshman   SD          Math     Lacrosse
   3 │ Anna          Female  1. Freshman   NC          English  Basketball
   4 │ Becky         Female  2. Sophomore  SD          Art      Baseball
   5 │ Benjamin      Male    4. Senior     WI          English  Basketball
```
