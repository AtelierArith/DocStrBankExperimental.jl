```
setup_ECCO4!(config::MITgcm_config)
```

Setup method for ECCO4 and OCCA2 solutions.

```
using MITgcm

params=read_toml(:ECCO4)
folder=joinpath(pwd(),"tmp1")

MC=MITgcm_config(inputs=params,folder=folder)

#providing executable (optional)
#push!(MC.inputs[:setup][:main],(:exe => joinpath(pwd(),"mitgcmuv")))

#providing input folder (optional)
#push!(MC.inputs[:setup][:main],(:input_folder => joinpath(pwd(),"input_folder")))

#modifying run time options (optional)
#MC.inputs[:pkg][:PACKAGES][:useECCO]=false

setup(MC)

#modifying build options (optional)
#MC.inputs[:setup][:build][:options]=MITgcm.build_options_pleiades

build(MC)

launch(MC)
```
