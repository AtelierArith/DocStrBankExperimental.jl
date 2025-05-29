```
Spectrum{T<:Real} <: AbstractVector{T}

Spectrum(energy::EnergyScale, data::Vector{<:Real}, props::Dict{Symbol,Any})
```

Construct a structure to hold spectrum data (energy scale, counts and metadata).

See [`NeXLSpectrum.EnergyScale`](@ref) or [`NeXLSpectrum.LinearEnergyScale`](@ref)

Example:

```
julia> spec = Spectrum(LinearEnergyScale(0.0,10.0),
                 collect(1:1024),
                 Dict{Symbol,Any}(:BeamEnergy=>10.0e3, :LiveTime=>30.0))
                                                                              ** 1024.0
                                                                       *********
                                                               *****************
                                                        ************************
                                                 *******************************
                                          **************************************
                                   *********************************************
                            ****************************************************
                     ***********************************************************
              ******************************************************************
       *************************************************************************
******************************************************************************** 10.0 keV
Spectrum[3062][10.0 keV, Unknown, 525000.0 counts]
```

Spectra are usually loaded from disk using:

```
s1 = loadspectrum(joinpath(path,"ADM-6005a_1.msa")) # Auto-detects the file type (supports ISO/EMSA, Bruker, ASPEX, ??? files)
  *                                                                                                  128860.0
  *
  *
  *
  *
  *
  *     *
  *     *
  *     *
  * ** **
  * ** *****        **  **
**************************************************************************************************** 20.0 keV
Spectrum{Float64}[ADM-6005a_1, -484.20818 + 5.01716⋅ch eV, 4096 ch, 20.0 keV, Unknown, 6.81e6 counts]
```

`Spectrum` implements indexing using various different mechanisms.  If `spec` is a `Spectrum` then

```
spec[123] # will return the number of counts in channel 123
spec[123:222] # will return a Vector of counts from channel 123:222
spec[134.] # will return the number of counts in the channel at energy 134.0 eV
spec[134.0:270.0] # will return a Vector of counts for channels with energies between 134.0 eV and 270.0 eV
spec[n"Ca L3-M5"] # Counts in the channel at the Ca L3-M5 characteristic X-ray energy
spec[:Comment] # will return the meta-data item named :Comment
```

Basic spectrum math is supported using the operators *, /, ÷, +, and -.  If `s1`, `s2` and `s3` are `Spectrum` objects then:

```
2*s1 # A Spectrum containing twice as many counts in each channel
2.0*s1 # A Spectrum containing twice as many counts in each channel
s1/2.0 # A spectrum containing half as many counts in each channel
s1÷2 # A spectrum containing half as many counts in each channel (Only works for Spectrum{<:Integer})
s1 + s2 # A Spectrum containing channel-by-channel sum of counts in s1 and s1 and common properties.
s1 - s2 # The channel-by-channel difference
```

Spectrum metadata is identified by a `Symbol`. These `Symbol`s are used within NeXLSpectrum. You can create others  to associate other data items with a `Spectrum`.

```
:BeamEnergy    # In eV
:Elevation     # In radians
:TakeOffAngle  # In radians (Detector position)
:Azimuthal     # In radians (Detector position)
:WorkingDistance # In cm (not mm!!!!)
:LiveTime      # In seconds
:RealTime      # In seconds
:DeadFraction  # Fractional
:ProbeCurrent  # In nano-amps
:Name          # A `String`
:Owner         # A `String`
:Sample        # Description of the sample
:StagePosition # A Dict{Symbol,Real} with entries :X, :Y, :Z, :R, :T, B: in cm and degrees
:Comment       # A `String`
:Composition   # A `Material` (known composition, not measured)
:Elements      # A collection of elements in the material like `[ n"Fe", n"Ca", n"Si" ]`
:Detector      # A Detector like a BasicEDS or another EDSDetector
:Filename      # Source filename
:Coating       # A `Film` or `Film[]` (eg. 10 nm of C|Au etc.)
:AcquisitionTime # Date and time of acquisition (`DateTime` struct)
:Signature     # Dict{Element,Real} with the "particle signature"
:SolidAngle    # Detector solid angle is steradians (area/dist²)
```

Spectrum Image items:

```
:ImageRotation # Rotation of the primary scan direction from the :X axis towards the :Y axis in radians
```

Less common items:

```
:ImageMag	   # Magnification (assuming a 3.5" image) of the first image
:ImageZoom     # Additional zoom for second image in a two image TIFF
:Operator      # Analyst in ASPEX TIFF files
:Image1, :Image2 ... # Images associated with the spectrum
:BrukerThroughtput # Nominal throughtput setting on a Bruker detector
:DetectorSerialNumber # EDS detector serial number
:DetectorModel # Vendor model name
:DetectorThickness # Thickness of detector active area
:DeadLayerThickness # Thickness of Si dead layer on the entrance surface of the detector
:Window        # Window construction details
:DetectorSolidAngle # Collection solid angle of the X-ray detector
:ChamberPressure # Vacuum presure in the sample chamber
:ChamberAtmosphere # Nominally the composition of the residual gas in the chamber
```

XRF related items:

```
:BeamEnergy  # Accelarating voltage within X-ray tube (eV)
:XRFTubeAnode    # Element from which the X-ray tube is constructed
:ProbeCurrent  # Electron current in the X-ray tube
:XRFTubeIncidentAngle # Incident angle of electron beam in tube
:XRFTubeTakeOffAngle # Take-off angle from tube
:XRFExcitationAngle # Angle of incidence of the X-ray beam on the sample
:XRFDetectionAngle # Angle of the detector relative to the sample
:XRFExcitationPathLength # Distance from X-ray source to sample
:XRFDetectionPathLength # Distance from the sample to the X-ray detector
:XRFSampleTilt    #  Additional tilt of the sample
:XRFTubeWindow   # Construction of the tube window
```

Not all spectra will define all properties.  Algorithms can define the `NeXLCore.minproperties(ty::Type)` method to specify which properties are required by an algorithm of `ty::Type`.  Then `hasminrequired` and `requiredbutmissing` methods will determine whether a `Spectrum` or `Dict{Symbol,Any}` is suitable for an algorithm.
