add*allcyclones!(addition :: Array{T,2}, buf :: Array{T,2},array :: Array{T,2},radius*bins,array :: Array{T,3},segmentedcyclones,cyclonescenters,gridspacing)

Compute the azimuthal average of some quantity around a center. Repeats the process and averages about all the tropical cyclones detected on the array. It receives an array with the radius bins to use,the field to average, called `array`, each cyclone as a SegmentedImage,the centers of the cyclones and the gridspacing.
