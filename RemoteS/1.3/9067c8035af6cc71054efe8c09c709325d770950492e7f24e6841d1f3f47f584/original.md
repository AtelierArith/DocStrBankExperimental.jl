```
model, classes = train_raster(cube::GItype, train::Union{Vector{<:GMTdataset}, String}; np::Int=0, density=0.1)
```

  * `cube`: The cube wtih band data to classify.
  * `train`: A vector of GMTdatasets or a file name of one containing the polygons used to train the model.  NOTE: The individual datasets MUST have associated an attribute called "class" containing the class name as a string.  This can be achieved for text data in the form of a GMT multi-segment file (one where segments are separated by the '>'  symbol) if the multi-segment separator line contains the text $Attrib(class=name)$
  * `np`: Number of points per polygon to be determined by $randinpolygon$
  * `density`: Alternative to `np`. See also the help of the $randinpolygon$ function.

Returns the trained model and the class names.
