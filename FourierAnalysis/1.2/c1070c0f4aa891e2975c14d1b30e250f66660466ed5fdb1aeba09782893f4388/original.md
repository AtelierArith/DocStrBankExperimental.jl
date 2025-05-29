```julia
function taper( kind  :: TaperKind,
                wl    :: Int;
            α       :: Real    = 2.,
            n       :: Int     = ceil(Int, 2*α)-1,
            padding :: Int     = 0,
            type    :: Type{T} = Float64) where T<:Union{Real, Complex}

```

Universal constructor of [Taper](@ref) objects, given a tapering window `kind`, of type [TaperKind](@ref) and the window length `wl`. NB: for the `hamming` and `blackman` type use `FourierAnalysis.hamming` and `FourierAnalysis.blackman`  to avoid conflicts with the DSP package.

Return a vector of length `wl` for all types of tapers, but for the dpss (Slepian multi-tapers), for which return a matrix of size `wl` x `n`.

If optional keyword argument `padding` is >0, then the actual window length will be `wl` + `padding`.

The `type` optional keyword argument can be use to specify the the type of elements of the typering window. By default, this is the `Float64` type.

Optional keywords arguments `α` and `n` currently apply only for slepian multi-tapering (*discrete prolate spheroidal sequences*):

`α` is the *half bandwidth* (hbw) parameter as per the DSP.jl package. This unit is used in many dpss implementations and it is often reported that "typical values" for `α` are 2, 2.5, 3, 3.5 or 4. However, the optimal smoothing increases with the ratio between window length and sampling rate, thus these values in absolute terms are not useful. In fact, the larger the *hbw* and the higher `n`, the smoother the spectra will be (variance reduction). In order to overcome these difficulties, for Slepian's multitapering *FourirAnalysis* implements the [`slepians`](@ref) constructor, which allows the bandwidth parameter to be given in Hz and the number of tapering windows to be chosen automatically.

`n` is the number of tapering windows. For slepian tapers this is the number of the discrete prolate spheroidal sequences. As in the DSP package, by default it is set to `ceil(Int, 2*α)-1`, however, depending on how large this number is, low eigenvalues may correspond to the last sequences, therefore those should be discarded.

**See**: [plot tapering windows](@ref).

**See also**: [`slepians`](@ref), [`taperinfo`](@ref)

**Examples**:

```julia
using FourierAnalysis

## Use the constructor
sr, t, f, a = 128, 128, 10, 0.5
# create a sinusoidal superimposed to white noise
v=sinusoidal(a, f, sr, t*16, 0) + randn(t*16)
# create a data matrix
X=broadcast(+, v, randn(t*16, 3))*randn(3, 3)
# compute spectra using hamming tapering window
# we need to prepend 'FourierAnalysis.' since `hamming`
# is declared also in DSP.jl
H=taper(FourierAnalysis.hamming, t)
S=spectra(X, sr, t; tapering=H)
# you can obtain the same thing with
S=spectra(X, sr, t; tapering=H)
# which will create the hamming tapering window on the fly,
# thus calling explicitly the constructor is interesting
# only if you need to reuse the same tapering window many times.

## Plot tapering windows using the standard plot function
using Plots
tapers=[TaperKind(i) for i=1:8]
X=zeros(t, 8)
for i=1:8 X[:, i] = taper(tapers[i], t).y end
mylabels=Array{String}(undef, 1, 8)
for i=1:8 mylabels[1, i]=string(tapers[i]) end
plot(X; labels=mylabels)

## using the recipe declared in recipes.jl
plot(taper(parzen, 256))
plot(taper(slepian, 256, α=4, n=7))

```
