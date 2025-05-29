Creates the KuramotoSivashinsky1D dataset,  images of size n*pixels x n*time, given

  * split: :train or :test
  * f: fraction of data desired
  * Tx: the float type. The dataset was created using Float32
  * n_pixels: the number of nodes in the spatial dimension                      Only 128 is supported currently.
  * n_time: the number of time samples to use when creating the 2d ``images".
