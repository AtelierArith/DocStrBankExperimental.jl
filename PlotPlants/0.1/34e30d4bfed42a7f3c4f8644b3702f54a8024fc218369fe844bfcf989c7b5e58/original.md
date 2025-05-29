```
save_gif!(figs::Array, fps::Int, gif::String)
save_gif!(imgs::Array{Array,1}, fps::Int, fn::String)
```

Save an array of figures as GIF, given

  * `figs` An array of figures
  * `fps` Frame per second
  * `fn` File name of the GIF to save
  * `imgs` An array of array (loaded figures)
