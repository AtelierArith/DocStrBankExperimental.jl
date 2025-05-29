```
disp(mri::MRI, mrimod::Union{MRI, Nothing}=nothing)
```

Quick display of an `MRI` structure (an image slice and a summary of header info) in the terminal window

# Arguments:

  * `mri::MRI`: the main image to display
  * `mrimod:MRI`: an optional image to modulate the main image by (e.g., an FA map to modulate a vector map)
