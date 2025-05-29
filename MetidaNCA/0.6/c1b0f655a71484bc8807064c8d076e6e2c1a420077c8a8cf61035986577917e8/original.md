```
nca!(data::PKSubject{T,O}; adm = :ev, calcm = :lint, intpm = nothing,  partials = nothing, prtext = :err, verbose = 0, warn = true, io::IO = stdout, modify! = nothing) where T where O
```

  * `adm` - administration:

      * `:ev` - extra vascular;
      * `:iv` - intravascular bolus;
  * `calcm` - AUC/AUMC calculation method:

      * `:lint` - linear trapezoidal;
      * `:luld` - linear up log down;
      * `:luldt` - linear up log down after Tmax;
      * `:logt` - log-trapezoidal after Tmax (Not Recommended);
  * `intpm` - interpolation method:

      * `:lint` - linear trapezoidal;
      * `:luld` - linear up log down;
      * `:luldt` - linear up log down after Tmax;
      * `:logt` - log-trapezoidal after Tmax;
      * `:calcm` - same as `calcm`;
  * `partials` - calculate partial AUC vor vector of time intervals (`:err` (default) - throw error if end time > last oservation time; `:last` - no extrapolation; `:extr` - if `Kel` calculated used extrapolation or `NaN` if no `Kel`);
  * `prtext` - extrapolation rule for partials AUC;
  * `verbose` - print to `io`, 1: partial areas table, 2: 1, and results;
  * `warn` - show warnings;
  * `io` - output stream;
  * `modify!` - function to modify output paramaters, call `modify!(ncaresult)` if difined.

Results:

  * Cmax
  * Tmax
  * Cdose
  * Tlag
  * Clast
  * AUClast
  * AUMClast
  * AUCall
  * Rsq
  * ARsq
  * Kel
  * HL
  * LZint
  * NpLZ
  * Clast_pred
  * AUCinf
  * AUCinf_pred
  * AUMCinf
  * AUMCinf_pred
  * AUCpct
  * MRTlast
  * MRTinf
  * MRTinf_pred
  * Cllast
  * Clinf
  * Vzlast
  * Vzinf
  * Vssinf

Steady-state parameters (tau used):

  * AUCtau
  * AUMCtau
  * Ctau
  * Cavg
  * Ctaumin
  * Accind
  * Fluc
  * Fluctau
  * Swing
  * Swingtau
  * MRTtauinf
  * Cltau
  * Vztau

`partials` is a vector of vectors, tuples or pairs. Example: `partials = [(1,2), (3,4)]`, `partials = [[1,2], (3,4)]`
