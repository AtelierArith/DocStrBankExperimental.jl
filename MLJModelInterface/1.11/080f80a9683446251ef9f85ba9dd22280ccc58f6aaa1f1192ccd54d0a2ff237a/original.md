```
metadata_model(T; args...)
```

Helper function to write the metadata for a model `T`.

## Keywords

  * `input_scitype=Unknown`: allowed scientific type of the input data
  * `target_scitype=Unknown`: allowed scitype of the target (supervised)
  * `output_scitype=Unknown`: allowed scitype of the transformed data (unsupervised)
  * `supports_weights=false`: whether the model supports sample weights
  * `supports_class_weights=false`: whether the model supports class weights
  * `load_path="unknown"`: where the model is (usually `PackageName.ModelName`)
  * `human_name=nothing`: human name of the model
  * `supports_training_losses=nothing`: whether the (necessarily iterative) model can report training losses
  * `reports_feature_importances=nothing`: whether the model reports feature importances

## Example

```julia
metadata_model(KNNRegressor,
    input_scitype=MLJModelInterface.Table(MLJModelInterface.Continuous),
    target_scitype=AbstractVector{MLJModelInterface.Continuous},
    supports_weights=true,
    load_path="NearestNeighbors.KNNRegressor")
```
