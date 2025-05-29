```
s3open(s3_url::AbstractString, mode::AbstractString="rb") -> file, io
```

Open a file from an S3 URL.

## Input arguments

  * `s3_url::AbstractString`: The S3 URL of the file.
  * `mode::AbstractString="rb"`: The access mode. Default is read-only in binary mode.

## Output arguments

  * `file`: A file-like NWB object
  * `io`: The io stream to the file. This should be `io.close()`d before exiting Julia.

## Examples

```julia
s3_url = "https://visual-behavior-neuropixels-data.s3.us-west-2.amazonaws.com/visual-behavior-neuropixels/behavior_ecephys_sessions/1044385384/ecephys_session_1044385384.nwb"
data = s3open(s3_url)
```
