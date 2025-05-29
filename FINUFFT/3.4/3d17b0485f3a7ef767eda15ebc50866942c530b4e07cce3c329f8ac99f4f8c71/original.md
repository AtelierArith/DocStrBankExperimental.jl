```
mutable struct nufft_opts
    modeord            :: Cint
    spreadinterponly   :: Cint
    debug              :: Cint
    spread_debug       :: Cint
    showwarn           :: Cint
    nthreads           :: Cint
    fftw               :: Cint
    spread_sort        :: Cint
    spread_kerevalmeth :: Cint
    spread_kerpad      :: Cint
    upsampfac          :: Cdouble
    spread_thread      :: Cint
    maxbatchsize       :: Cint
    spread_nthr_atomic :: Cint
    spread_max_sp_size :: Cint
    fftw_lock_fun      :: Ptr{Cvoid}
    fftw_unlock_fun    :: Ptr{Cvoid}
    fftw_lock_data     :: Ptr{Cvoid}
end
```

Options struct passed to the FINUFFT library.

# Fields

This is a summary only; see FINUFFT documentation for full descriptions.

```
modeord :: Cint
```

0: CMCL-style increasing mode ordering (neg to pos), or
1: FFT-style mode ordering (affects type-1,2 only)

```
spreadinterponly :: Cint
```

(type 1,2 only) 
0: do actual NUFFT 
1: only spread (if type 1) or interpolate (type 2) 
     debug :: Cint 0 silent, 1 some timing/debug, or 2 more

```
spread_debug :: Cint
```

spreader: 0 silent, 1 some timing/debug, or 2 tonnes

```
showwarn :: Cint
```

0 don't print warnings to stderr, 1 do

```
nthreads :: Cint
```

number of threads to use, or 0 uses all available

```
fftw :: Cint
```

plan flags to FFTW (FFTW*ESTIMATE=64, FFTW*MEASURE=0,...)

```
spread_sort :: Cint
```

spreader: 0 don't sort, 1 do, or 2 heuristic choice

```
spread_kerevalmeth :: Cint
```

spreader: 0 exp(sqrt()), 1 Horner piecewise poly (faster)

```
spread_kerpad :: Cint
```

(exp(sqrt()) only): 0 don't pad kernel to 4n, 1 do

```
upsampfac :: Cdouble
```

upsampling ratio sigma: 2.0 std, 1.25 small FFT, 0.0 auto

```
spread_thread :: Cint
```

(vectorized ntr>1 only)
0: auto
1: seq multithreaded
2: parallel single-thread spread

```
maxbatchsize :: Cint
```

(vectorized ntr>1 only): max transform batch, 0 auto

```
spread_nthr_atomic :: Cint
```

if >=0, threads above which spreader OMP critical goes atomic

```
spread_max_sp_size :: Cint
```

if >0, overrides spreader (dir=1) max subproblem size

```
fftw_lock_fun      :: Ptr{Cvoid}
```

Function ptr that locks the FFTW planner 
C signature: `void (*fftw_lock_fun)(void *)`

```
fftw_unlock_fun    :: Ptr{Cvoid}
```

Function ptr that unlocks the FFTW planner 
C signature: `void (*fftw_unlock_fun)(void *)`

```
fftw_lock_data     :: Ptr{Cvoid}
```

Data to pass to the lock functions (e.g. a mutex) 
C signature: `void *fftw_lock_data`
