```julia
run_model_epochs(
    inmodel::EasyABM.SpaceModel3D;
    steps_per_epoch,
    num_epochs,
    step_rule,
    save_to_folder
)

```

Runs the simulation for `num_epochs` number of epochs where each epoch consists of `steps_per_epoch` number of steps. The model for each epoch is a deepcopy of the input model and is saved as .jld2 file.
