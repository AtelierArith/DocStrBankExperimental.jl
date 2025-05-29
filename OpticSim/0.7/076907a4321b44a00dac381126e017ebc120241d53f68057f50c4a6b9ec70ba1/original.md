```
HologramInterface{T} <: OpticalInterface{T}
```

Interface representing a *thick* hologram (though geometrically thin). The efficiency, `η`, is calculated using Kogelnik's coupled wave theory so is only valid for the first order. If the zero order is included then it has efficiency `1 - η`. Also assumes that the HOE was recorded under similar conditions to the playback conditions, `thickness` is in microns.

`BeatState` arguments can be one of `ConvergingBeam`, `DivergingBeam` and `CollimatedBeam`. In the first two cases `signalpointordir` and `referencepointordir` are 3D point in global coordinate space. For `CollimatedBeam` they are normalized direction vectors.

For reference, see:

  * *Coupled Wave Theory for Thick Hologram Gratings* - H Kogelnik, 1995
  * *Sequential and non-sequential simulation of volume holographic gratings* - M Kick et al, 2018

```julia
HologramInterface(signalpointordir::SVector{3,T}, signalbeamstate::BeamState, referencepointordir::SVector{3,T}, referencebeamstate::BeamState, recordingλ::T, thickness::T, beforematerial, substratematerial, aftermaterial, signalrecordingmaterial, referencerecordingmaterial, RImodulation::T, include0order  = false)
```
