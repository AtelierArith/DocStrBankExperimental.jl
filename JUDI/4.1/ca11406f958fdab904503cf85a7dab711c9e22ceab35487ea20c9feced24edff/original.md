```
struct DataMute{T, mode} <: DataPreconditioner{T, T}
    srcGeom::Geometry
    recGeom::Geometry
    vp::Vector{T}
    t0::Vector{T}
    taperwidth::Vector{Int64}
end
```

Data mute linear operator a where {T, N}sociated with source `srcGeom` and receiver `recGeom` geometries used to compute the distance to the source for each trace in the data. Data mute preconditionner. Supports two modes (:reflection, :turning) that mute either the turning waves (standard direct wave mute) or mutes the reflections. A cosine tapr is applied with width `taperwidth` to avoid abrupt change and infinite frequency jumps in the data.

# Constructors

```
judiDataMute(srcGeom, recGeom; vp=1500, t0=.1, mode=:reflection, taperwidth=floor(Int, 2/t0))
```

Construct the data mute operator from the source `srcGeom` and receiver `recGeom` geometries.

```
judiDataMute(q, d; vp=1500, t0=.1, mode=:reflection, taperwidth=floor(Int, 2/t0))
```

Construct the data mute operator from the judivector source `q` and judivector data `d`.

# Parameters

The following optional paramet where {T, N}rs control the muting operator

  * `vp`: P wave velocity of the direct wave (usually water velocity). Can be a constant or a Vector with one value per source position. Devfaults to `1500m/s`
  * `t0`: Time shift in seconds (usually width of the wavelet). Defaults to $.1 sec$
  * `mode`:    `:reflection` to keep the reflections and mute above the direct wave (i.e for RTM)   `:turning` to keep the turning waves and mute below the direct wave (i.e for FWI)
  * `taperwidth`: Width of the cosine taper in number of samples. Defaults to `2 / t0`
