```
runsim(dt, tmax, A, H; 
	method=:TDVP1, 
	machine=LocalMachine(), 
	params=[], 
	obs=[], 
	convobs=[],
            convparams=error("Must specify convergence parameters"),
            save=false,
            plot=save,
            savedir=string(homedir(),"/MPSDynamics/"),
            unid=randstring(5),
            name=nothing,
	kwargs...
	)
```

Propagate the MPS `A` with the MPO `H` up to time `tmax` in time steps of `dt`. The final MPS is returned to `A` and the measurement data is returned to `dat` 

# Arguments

  * `method`: Several methods are implemented in MPSDynamics. `:TDVP1` refers to 1-site TDVP on tree and chain MPS, `:TDVP2` refers to 2-site TDVP on chain MPS, `:DTDVP` refers to a variant of 1-site TDVP with dynamics bond-dimensions on chain MPS
  * `machine`: `LocalMachine()` points local ressources, `RemoteMachine()` points distant ressources
  * `params`: list of parameters written in the log.txt file to describe the dynamics. Can be listed with @LogParams().
  * `obs`: list of observables that will be measured at every time step for the most accurate convergence parameter supplied to `convparams`
  * `convobs`: list of observables that will be measure at every time step for every convergence parameter supplied to `convparams`
  * `convparams`: list of convergence parameter with which the propagation will be calculated for every parameter. At each parameter, `convobs` are measured while `obs` are measured only for the most accurate dynamics
  * `save`: Used to choose whether the data will also be saved to a file
  * `plot`: Used to choose whether plots for 1D observables will be automatically generated and saved along with the data
  * `savedir`: Used to specify the path where resulting files are stored
  * `unid`: Used to specify the name of the directory containing the resulting files
  * `name`: Used to describe the calculation. This name will appear in the log.txt file
