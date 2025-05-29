A lightweitht julia wrapper for [WORLD](https://github.com/mmorise/World), a high-quality speech analysis, manipulation and synthesis system. WORLD provides a way to decompose a speech signal into:

  * Fundamental frequency (F0)
  * spectral envelope
  * aperiodicity

and re-synthesize a speech signal from these paramters. Please see the project page for more details on the WORLD.

!!! note
    WORLD.jl is based on a fork of WORLD ([r9y9/World-cmake](https://github.com/r9y9/World-cmake)).


[https://github.com/r9y9/WORLD.jl](https://github.com/r9y9/WORLD.jl)

## Usage

In the following examples, suppose `x::Vector{Float64}` is a input monoral speech signal like:

![](assets/x.png)

### F0 estimation

#### Harvest

```julia
opt = HarvestOption(71.0, 800.0, period)
f0, timeaxis = harvest(x, fs, opt)
```

![](assets/f0_by_harvest.png)

#### Dio

```julia
opt = DioOption(f0floor=71.0, f0ceil=800.0, channels_in_octave=2.0,
        period=period, speed=1)
f0, timeaxis = dio(x, fs, opt)
```

![](assets/f0_by_dio.png)

#### StoneMask

```julia
f0 = stonemask(x, fs, timeaxis, f0)
```

![](assets/f0_refinement.png)

### Spectral envelope estimation by CheapTrick

```julia
spectrogram = cheaptrick(x, fs, timeaxis, f0)
```

![](assets/envelope_by_cheaptrick.png)

### Aperiodicity ratio estimation by D4C

```julia
aperiodicity = d4c(x, fs, timeaxis, f0)
```

![](assets/aperiodicity_by_d4c.png)

### Synthesis

```julia
y = synthesis(f0, spectrogram, aperiodicity, period, fs, length(x))
```

![](assets/synthesis.png)

### Compact speech parameterization

Raw spectrum envelope and aperiodicity spectrum are relatively high dimentional (offen more than 513 or 1025) so one might want to get more compact representation. To handle this situation, WORLD provides coding/decoding APIs for spectrum envelope and aperiodicity. Additionally, WORLD.jl provides conversions from spectrum envelope to mel-cepstrum and vice versa. You can choose any of coding/decoding APIs depends on your purpose.

#### spectrum envelope to mel-cepstrum

```julia
mc = sp2mc(spectrogram, order, α) # e.g. order=40, α=0.41
```

where `order` is the order of mel-cepstrum (except for 0th) and α is a frequency warping parameter.

![](assets/melcepstrum.png)

#### mel-cepstrum to spectrum envelope

```julia
approximate_spectrogram = mc2sp(mc, α, get_fftsize_for_cheaptrick(fs))
```

![](assets/envelope_reconstructed_from_melcepstrum.png)

#### Code aperiodicity

```julia
coded_aperiodicity = code_aperiodicity(aperiodicity, fs)
```

![](assets/coded_aperiodicity.png)

#### Decode aperiodicity

```julia
decoded_aperiodicity = decode_aperiodicity(coded_aperiodicity, fs)
```

![](assets/decoded_aperiodicity.png)

For the complete code of visualizations shown above, please check [the IJulia notebook](http://nbviewer.jupyter.org/github/r9y9/WORLD.jl/blob/master/docs/src/assets/WORLD-demo.ipynb).

## Exports

  * [`CheapTrickOption`](@ref)
  * [`D4COption`](@ref)
  * [`DioOption`](@ref)
  * [`HarvestOption`](@ref)
  * [`cheaptrick`](@ref)
  * [`code_aperiodicity`](@ref)
  * [`code_spectral_envelope`](@ref)
  * [`d4c`](@ref)
  * [`decode_aperiodicity`](@ref)
  * [`decode_spectral_envelope`](@ref)
  * [`dio`](@ref)
  * [`get_fftsize_for_cheaptrick`](@ref)
  * [`get_number_of_aperiodicities`](@ref)
  * [`harvest`](@ref)
  * [`interp1`](@ref)
  * [`interp1!`](@ref)
  * [`mc2sp`](@ref)
  * [`sp2mc`](@ref)
  * [`stonemask`](@ref)
  * [`synthesis`](@ref)
