This documentation should help you figure out what you have access to

  * "dx" and "dy" are the x and y limit differentials
  * "img_arr" is the raw data of all frames
  * "red_zstack" is the red channel of the image array
  * "grn_zstack" is the green channel of the image array
  * "red*zproj" and "grn*zproj" are the red and green zprojection (taken with mean function)
  * "red*img" and "grn*img" are those zprojections made into RGB{Float32} images
  * "composite_img" is a composite of the red and grn images
  * "red*trace" and "grn*trace" are the traces of the mean fluoresence by frame
  * "dff*red*zstack" is the delta f/f (f0-f)/f taken of by a rolling mean
  * "dff*grn*zstack" is the dff taken using just the total mean of the trace
  * "dff*red*comp*zstack" and "dff*grn*comp*zstack" are the RGB{Float32} versions
  * "dff*composite*zstack" is the composite
  * "dff*red*zproj" and "dff*grn*zproj" are the zstack projections of the dff images
  * "dff*red*img" and "dff*grn*img" are the image versions of the red and green z projections
  * "dff*composite*img" is the composite of the red and green images
  * "dff*red*trace" and "dff*grn*trace" are the trace versions
  * "pks*vals" are the maxima peaks and valleys of the dff*green_trace
  * "grn*row*sums" is the sum of all green section rows
  * "grn*sect*arr" and "red*sect*arr" are the arrays formed as a result of the peakfinding
