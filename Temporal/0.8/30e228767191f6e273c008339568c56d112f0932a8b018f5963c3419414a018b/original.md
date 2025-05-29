```
tsread(file::String;dlm::Char=',',header::Bool=true,eol::Char='\n',indextype::Type=Date,format::String="yyyy-mm-dd")::TS
```

Read contents from a text file into a TS object.

# Arguments

  * `file::String`: path to the input file

Optional args:

  * `dlm::Char=','`: delimiter used to separate columns
  * `header::Bool=true`: whether a header row exists
  * `eol::Char='\n'`: character used to specify ends of lines
  * `indextype::Type=Date`: DateTime or Date
  * `format::String="yyyy-mm-dd"`: format used to parse the index

# Example

```
X = tsread("data.csv")
```
