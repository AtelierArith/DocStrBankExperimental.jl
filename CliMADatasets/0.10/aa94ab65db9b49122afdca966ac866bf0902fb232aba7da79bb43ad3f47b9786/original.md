Creates the CorrelatedOU1D dataset, images of size n*pixels x n*time, given

  * split: :train or :test
  * f: fraction of data desired
  * Tx: the float type. The dataset was created using Float32
  * n*pixels: the spatial extent of the box used in the simulation           Note that: Δx = 1; so n*pixels is the size of the box.                      Only 64 is supported currently.
  * n_time: the number of time samples to use when creating the 2d ``images".
