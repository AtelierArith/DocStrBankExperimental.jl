```
annotation([plotobj::DisplazWindow,] coords::Array{T,1}, text::String, label=text::String)
```

Place a text annotation at given coordinates

If not specified, `plotobj` is the current plot window.  coords is a three element array [x, y, z], text is the text to plot and label its Displaz label, note annotation labels don't appear in Displaz's list of data sets they are needed however to unload an annotation. If unspecified the label defaults to the annotation string.
