SeisSpitzFX(d;<keyword arguments>)

First order f-x interpolation using Spitz' method.   Input size is size(d)= (nt,nh). Output size is (nt,2*nh-1)

# Arguments

-`dt`: sampling interval in secs -`npf`: prediction filter length

  * `pre1` : percentage of pre-whitening for Pef estimation
  * `pre2` : percentage of pre-whitening for estimation of missing samples
  * `flow` : minimun temporal frequency to reconstruct (Hz)
  * `fhigh` : maximun temporal frequency to reconstruct (Hz)

# Example

'''julia d_interp = SeisSpitzFX(d) '''

  * Reference: Spitz, S., 1991, Seismic trace interpolation in the F-X domain: Geophysics, 56, 785-794.
