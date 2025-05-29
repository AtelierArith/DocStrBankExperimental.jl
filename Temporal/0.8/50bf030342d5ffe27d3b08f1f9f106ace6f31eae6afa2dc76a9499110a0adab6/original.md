```
tswrite(x::TS,file::String;dlm::Char=',',header::Bool=true,eol::Char='\n')::Nothing
```

Write time series data to a text file.

# Arguments

  * `x::TS`: time series object to write to a file
  * `file::String`: filepath to which object shall be written

Optional args:

  * `dlm::Char=','`: delimiter used to separate columns
  * `header::Bool=true`: whether the object's `fields` member should be included as a header row in the output file
  * `eol::Char='\n'`: character used to specify ends of lines

# Example

```
X = TS(randn(252, 4))
tswrite(X, "data.csv")
```
