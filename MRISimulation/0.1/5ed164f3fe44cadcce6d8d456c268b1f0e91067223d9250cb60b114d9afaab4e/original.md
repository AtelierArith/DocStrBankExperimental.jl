```
simulation(seq::AbstractSequence, tr::Vector{Trajectory}, image::Array{T,3}
                ; opName="fast", r1map=[], r2map=[], fmap=[], senseMaps=[]
                , verbose=true, kargs...) where T<:Complex{<:AbstractFloat}
```

Simulate k-space data for all echoes of a pulse sequence. The echo intensities are simulated using the EPG formalism The Fourier integrals can be evaluated exactly or using NFFT

...

# Arguments

  * `seq::AbstractSequence`      - pulse sequence
  * `tr::Vector{Trajectory}`     - trajectories for all contrasts
  * `image::Array{T,3}` - image to be transformed
  * (`r1map=[]`)                 - R1 map of the object (real)
  * (`r2map=[]`)                 - R2 map of the object (real) / (R2* for GRE sequences)
  * (`fmap=[]`)                  - fieldmap (real)
  * (`opName="fast")             - name of operator to use ("explicit" or "fast")
  * (`sensmaps=[]`)              - array of coil sensitivities
  * (`verbose=true`)             - prints the progress if true
  * `kargs...`                   - addional keyword arguments

...
