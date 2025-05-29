```
I = classify(cube::GItype, train::Union{Vector{<:GMTdataset}, String}) -> GMTimage
```

  * `cube`: The cube wtih band data to classify.
  * `train`: A vector of GMTdatasets or a file name of one containing the polygons used to train the model.  NOTE: The individual datasets MUST have associated an attribute called "class" containing the class name as a string.  This can be achieved for text data in the form of a GMT multi-segment file (one where segments are separated by the '>'  symbol) if the multi-segment separator line contains the text $Attrib(class=name)$

Returns an image with the classification results where each class name was assigned a different integer number. That colorized image can plotted with $viz(I, colorbar=true)$.
