```
calculateSWI(data::Data, options::Options=Options())
```

Returns the calculated SWI using 'data' and 'options'.

# Examples

```julia-repl
julia> TEs = [4,8,12]
julia> data = Data(mag, phase, header(mag), TEs);
julia> swi = calculateSWI(data);
```

# With Options

Base.Docs.DocStr(svec("    Options(;   mag*combine=:SNR,\n                mag*sens=nothing,\n                mag*softplus=true,\n                phase*unwrap=:laplacian,\n                phase*hp*sigma=[4,4,0],\n                phase*scaling*type=:tanh,\n                phase*scaling*strength=4,\n                writesteps=nothing)\n\n* `mag_combine` selects the echo combination for the magnitude. Options are \n    * `:SNR`\n    * `:average`\n    * `:last` to select the last echo\n    * `(:CNR => (:gm, :wm))` to optimize the contrast between two selected tissues with the possible tissues classes to select in `src/tissue.jl`, currently only working for 7T\n    * `(:echo => 3)` to select the 3rd echo \n    * `(:closest => 15.3)` to select the echo that is closest to 15.3 ms \n    * `(:SE => 15.3)` to simulate the contrast that would be achieved using a corresponding single-echo scan with 15.3 ms echo time.\n\n* If `mag_sens` is set to an array, it is used instead of CLEAR-SWI sensitivity estimation. This can also be set to `mag_sens=[1]` to use the constant sensitivity of 1 and effectively avoid sensitivity correction. To change the sigma*mm value of the expected bias field size, set it to i.e. `mag*sens=(:sigma*mm => 7)`. The default is 7mm.\n\n* To deactivate scaling of the combined magnitude with the softplus function, use`mag*softplus=false`.\n\n*`phase*unwrap`is either`:laplacian`,`:romeo`, or`:laplacianslice`(slicewise laplacian unwrapping)\n\n* The`phase*hp*sigma`is used for high-pass filtering and is given in voxel for the [x,y,z]-dimension.  \n\n*`phase*scaling*type`is the scaling function to create the phase mask and can be`:tanh`or`:negativetanh`for sigmoidal filtering, or`:positive`,`:negative`, and`:triangular`for traditional SWI application.\n\n*`phase*scaling*strength`adjusts the strength of the created phase mask. A higher`phase*scaling*strength`is a stronger phase appearance. With a traditional SWI`phase*scaling*type`it corresponds to the power or number of phase mask multiplications.\n\n* Set`writesteps`to the path, where intermediate steps should be saved, e.g.`writesteps=\"/tmp/clearswi*steps\"`. If set to`nothing`, intermediate steps won't be saved.\n\n* Set`qsm` to true\n"), nothing, Dict{Symbol, Any}(:typesig => Union{}, :module => CLEARSWI, :linenumber => 20, :binding => CLEARSWI.Options, :path => "/home/terasaki/.julia/packages/CLEARSWI/TpwBe/src/utility.jl", :fields => Dict{Symbol, Any}()))

# Examples

```julia-repl
julia> TEs = [4,8,12]
julia> data = Data(mag, phase, header(mag), TEs);
julia> options = Options(phase_hp_sigma=[10,10,5], mag_softplus=false)
julia> swi = calculateSWI(data, options);
```
