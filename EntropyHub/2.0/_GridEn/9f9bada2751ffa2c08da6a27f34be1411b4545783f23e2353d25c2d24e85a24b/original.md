```
   GDE, GDR, _ = GridEn(Sig)
```

Returns the gridded distribution entropy (`GDE`) and the gridded     distribution rate (`GDR`) estimated from the data sequence (`Sig`) using     the default  parameters:    grid coarse-grain = 3, time delay = 1, logarithm = base 2

```
   GDE, GDR, PIx, GIx, SIx, AIx = GridEn(Sig)
```

In addition to GDE and GDR, GridEn returns the following indices     estimated for the data sequence (`Sig`) using the default  parameters:    [`PIx`]   - Percentage of points below the line of identity (LI)    [`GIx`]   - Proportion of point distances above the LI    [`SIx`]   - Ratio of phase angles (w.r.t. LI) of the points above the LI    [`AIx`]   - Ratio of the cumulative area of sectors of points above the LI

```
   GDE, GDR, ..., = GridEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=3, tau::Int=1, Logx::Real=exp(1), Plotx::Bool=false)
```

Returns the gridded distribution entropy (`GDE`) estimated from the data     sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Grid coarse-grain (m x m sectors), an integer > 1 

`tau`   - Time Delay, a positive integer    

`Logx`  - Logarithm base, a positive scalar 

`Plotx` - When Plotx == true, returns gridded Poicaré plot and a bivariate               histogram of the grid point distribution (default: false)  

# See also `PhasEn`, `CoSiEn`, `SlopEn`, `BubbEn`, `MSEn`

# References:

```
   [1] Chang Yan, et al.,
           "Novel gridded descriptors of poincaré plot for analyzing 
           heartbeat interval time-series." 
           Computers in biology and medicine 
           109 (2019): 280-289.

   [2] Chang Yan, et al. 
           "Area asymmetry of heart rate variability signal." 
           Biomedical engineering online 
           16.1 (2017): 1-14.

   [3] Alberto Porta, et al.,
           "Temporal asymmetries of short-term heart period variability 
           are linked to autonomic regulation." 
           American Journal of Physiology-Regulatory, Integrative and 
           Comparative Physiology 
           295.2 (2008): R550-R557.

   [4] C.K. Karmakar, A.H. Khandoker and M. Palaniswami,
           "Phase asymmetry of heart rate variability signal." 
           Physiological measurement 
           36.2 (2015): 303.
```
