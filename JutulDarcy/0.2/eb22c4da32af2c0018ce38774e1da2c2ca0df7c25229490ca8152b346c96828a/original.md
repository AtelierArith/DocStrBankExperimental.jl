```
setup_reservoir_model(reservoir::DataDomain, model_template::MultiModel; wells = [])
setup_reservoir_model(model_template::MultiModel; wells = [])
```

Set up a reservoir model with another model as a template. The template model is used to define the parameters and variables so that the resulting model is as similar to the original model as possible. The main purpose of this model is to "resetup" a model with for example a new set of wells.

It is also possible to pass a `reservoir` domain to set up the model with a new domain and new wells, copying over properties and secondary variables.

Note that the transfer process is not perfect and some variables might not be copied correctly if you are using a highly customized model. For instance, the treatment of regions is quite simple as it is based on the field name `region` that is initialized to one for each cell.
