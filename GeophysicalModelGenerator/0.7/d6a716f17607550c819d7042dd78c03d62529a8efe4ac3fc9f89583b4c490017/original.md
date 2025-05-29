```
download_data(url::String, local_filename="temp.dat"; dir=pwd(), maxattempts=5 )
```

Downloads a remote dataset with name `url` from a remote location and saves it to the current directory. If download fails, we make `maxattempts` attempts before giving up.

# Example

```julia
julia> url  = "https://seafile.rlp.net/f/10f867e410bb4d95b3fe/?dl=1";
julia> download_data(url)
"/Users/kausb/.julia/dev/GeophysicalModelGenerator/temp.dat"
```
