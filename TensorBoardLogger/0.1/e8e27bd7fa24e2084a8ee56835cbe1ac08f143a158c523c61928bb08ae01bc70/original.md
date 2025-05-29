```
log_embeddings(logger::TBLogger, name::AbstractString, mat::AbstractMatrix; metadata, metadata_header, img_labels, step=step(logger))
```

Log embedding data to tensorboard and visualize in 3-D or 2-D with PCA, t-SNE or UMAP.

  * mat: 2-D `Matrix` of data, with rows representing the samples and columns representing the features
  * metadata: Array of labels for each sample. Each element across 1st dimenstion will be converted to `string`
  * metadata_header: 1-D Array. Useful when samples have multiple labels. size should be same as size of each row in `metadata`
  * img_labels: TBImages object representing image labels for each sample.

      * each number of images (N) must be equal to number of samples in `mat`
      * each image must be a square (H == W)
      * the value √N * W must be less than or equal to 8192 because of tensorboard restrictions.
