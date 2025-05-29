```
simulation(tr::Trajectory, image::Array{T}, correctionMap = []; opName="fast"
          , senseMaps=[], verbose=true, kargs...) where T<:Complex{<:AbstractFloat}
```

Transforms a given image to k-space Domain. Dispatches whether the trajectory is 2d or 3d The Fourier integrals can be evaluated exactly or using NFFT Returns the demodulated signal.

...

# Arguments

  * `tr::Trajectory`             - three-dimensional Trajectory
  * `image::Array{T,3}` - image to be transformed
  * (`correctionMap=[]`)         - sum of the field offresonance (imaginary) map and relaxation map (real)
  * (`opName="fast")             - name of operator to use ("explicit" or "fast")
  * (`sensmaps=[]`)              - array of coil sensitivities
  * (`verbose=true`)             - prints the progress if true
  * `kargs...`                   - addional keyword arguments

...
